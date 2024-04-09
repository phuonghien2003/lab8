
var arrNam = [
    {
        id: 1,
        name: "The Cosmo(white)",
        code: "TC01345",
        price: "250.000",
        image: "https://down-vn.img.susercontent.com/file/1696316d79f933c12cc6015182a36e10",
    },
    {
        id: 2,
        name: "Quần babi",
        code: "TC013442",
        price: "550.000",
        image: "https://routine.vn/media/amasty/webp/catalog/product/cache/d0cf4470db45e8932c69fc124d711a7e/q/u/quan-short-nam-4-10s24psh029-black-_1__1_jpg.webp",
    },
    {
        id: 3,
        name: "Quan tây nam ",
        code: "TC0134342",
        price: "130.000",
        image: "https://down-vn.img.susercontent.com/file/1696316d79f933c12cc6015182a36e10",
    },
    {
        id: 4,
        name: "Quần jean",
        code: "TC013324",
        price: "250.000",
        image: "https://routine.vn/media/amasty/webp/catalog/product/cache/d0cf4470db45e8932c69fc124d711a7e/q/u/quan-short-nam-4-10s24psh029-black-_1__1_jpg.webp",
    },
    {
        id: 5,
        name: 'Thắt lưng nam da cao cấp ',
        code: 'MVN05',
        price: "250.000",
        image: "https://down-vn.img.susercontent.com/file/vn-11134207-7r98o-lpfn82x8ovv2a2",
    },
    {
        id: 6,
        name: 'Áo sơ mi nam basic',
        code: 'MVN06',
        price: "250.000",
        image: "https://down-vn.img.susercontent.com/file/sg-11134201-23010-uc3sy3gvivlvbb",
    },

    {
        id: 7,
        name: 'Áo Thun Polo Nam BL',
        code: 'MVN03',
        price: "250.000",
        image: "https://down-vn.img.susercontent.com/file/sg-11134201-23010-zvs6p52ndwmve6",
    },
    {
        id: 8,
        name: 'Áo Polo Nam Cổ Bẻ Thun',
        code: 'MVN04',
        price: "250.000",
        image: "https://down-vn.img.susercontent.com/file/743050d3c10a59f1b911810ead366116",
    },
];

function savelocalstorage() {
    localStorage.setItem('arrNam' ,JSON.stringify(arrNam));
}

function LoadlocalStorage() {
    var arrNamStr = localStorage.getItem('arrNam');
    if (arrNamStr) {
        arrNam = JSON.parse(arrNamStr);
    }
}

LoadlocalStorage();

function save(){
    var a = {
        id: document.getElementById('id').value,
        name: document.getElementById('name').value,
        code: document.getElementById('code').value,
        price: document.getElementById('price').value,
        image: document.getElementById('image').value,
    }    
    arrNam.push(a);
    savelocalstorage();
    console.log(a);
    show();
}


function showman() {
    var html = '';
    for (var i = 0; i < arrNam.length; i++) {
        html += "<tr>";
        html += "<td>" + (i + 1) + "</td>";
        html += "<td>" + arrNam[i].id + "</td>";
        html += "<td>" + arrNam[i].name + "</td>";
        html += "<td>" + arrNam[i].code + "</td>";
        html += "<td>" + arrNam[i].price + "</td>";
        html += "<td><img src='" + arrNam[i].image + "' alt='Hình ảnh' style='width: 50px; height: 50px;'></td>";
        html += "<td><button class='btn btn-info' onclick='editProduct(" + i + ")'>Cập nhật</button></td>";
        html += "<td><button class='btn btn-danger' onclick='deleteProduct(" + i + ")'>Xóa</button></td>";
        html += "</tr>";
    }
    document.getElementById('tblman').innerHTML = html;
}

function editProduct(index) {
    var product = arrNam[index];
    document.getElementById('id').value = product.id;
    document.getElementById('name').value = product.name;
    document.getElementById('code').value = product.code;
    document.getElementById('price').value = product.price;
    document.getElementById('image').value = product.image;
}

function deleteProduct(index) {
    var confirmDelete = confirm("Bạn có chắc muốn xóa sản phẩm này không?");
    if (confirmDelete) {
        arrNam.splice(index, 1);
        savelocalstorage();
        showman();
        reset();
    }
}


function reset(){
    document.getElementById('id').value='';
    document.getElementById('name').value='';
    document.getElementById('code').value='';
    document.getElementById('price').value='';
    document.getElementById('image').value='';
}

function show() {
    showman();
}

function update() {
    var idToUpdate = document.getElementById('id').value;
    for (var i = 0; i < arrNam.length; i++) {
        if (idToUpdate == arrNam[i].id) {
            arrNam[i].name = document.getElementById('name').value;
            arrNam[i].code = document.getElementById('code').value;
            arrNam[i].price = document.getElementById('price').value;
            arrNam[i].image = document.getElementById('image').value;
            savelocalstorage();
            showman();
            reset(); // Cập nhật xong thì reset các trường nhập liệu
            return;  // Kết thúc hàm nếu đã cập nhật thành công
        }
    }
    console.log("Không tìm thấy phần tử cần cập nhật.");
}

// function delete1() {
//     var idToDelete = document.getElementById('id').value;
//     console.log(idToDelete);

//     for (var i = 0; i < arrNam.length; i++) {
//         if (idToDelete == arrNam[i].id) {
//             arrNam.splice(i, 1); 
//             showman(); 
//             reset(); 
//             return; 
//         }
//     }

//     console.log("Không tìm thấy phần tử cần xóa.");
// }

//tạo trang home
function listProducts() {
    for (let i = 0; i <= arrNam.length - 1; i++) {
        var demo = '<div class="col-3">';
        demo += '<div class="card" style="width: 18rem;">';
        demo += '<img src="' + arrNam[i].image + '" class="card-img-top" style="height: 400px;">';
        demo += '<div class="card-body">';
        demo += '<h5 class="card-title">' + arrNam[i].name + '</h5>';
        demo += '<p class="card-text">' + arrNam[i].price + '</p>';
        demo += '<a href="#" class="btn btn-primary" onclick="order()">Đặt mua</a>';
        demo += '</div>'; 
        demo += '</div>';
        demo += '</div>';
        console.log(demo);
        document.getElementById("men").innerHTML += demo;
    }
}


//tạo thanh tìm kiếm
function searchProducts() {
    var input = document.getElementById('searchInput').value.toLowerCase(); // Lấy giá trị từ trường nhập liệu và chuyển thành chữ thường để so sánh không phân biệt chữ hoa/chữ thường
    var filteredProducts = arrNam.filter(function(product) { // Sử dụng phương thức filter để lọc các sản phẩm dựa trên điều kiện tìm kiếm
        return product.name.toLowerCase().includes(input) || // Tìm kiếm theo tên sản phẩm
               product.code.toLowerCase().includes(input) || // Tìm kiếm theo mã sản phẩm
               product.price.toLowerCase().includes(input);   // Tìm kiếm theo giá sản phẩm
    });
    // Hiển thị danh sách sản phẩm sau khi lọc
    displayProducts(filteredProducts);
}

// hiển thị danh sách sau khi tìm kiếm
function displayProducts(products) {
    var html = '';
    for (var i = 0; i < products.length; i++) {
        html += "<div class='col-3'>";
        html += "<div class='card' style='width: 18rem;'>";
        html += "<img src='" + products[i].image + "' class='card-img-top' style='height: 300px; object-fit: cover;'>";
        html += "<div class='card-body'>";
        html += "<h5 class='card-title'>" + products[i].name + "</h5>";
        html += "<p class='card-text'>" + products[i].price + "</p>";
        html += "<a href='#' class='btn btn-primary' onclick='order()'>Đặt mua</a>";
        html += "</div>"; 
        html += "</div>";
        html += "</div>";
    }
    document.getElementById("men").innerHTML = html;
}
