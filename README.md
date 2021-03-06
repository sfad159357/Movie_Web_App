部署在heroku的網站：
  https://infinite-hamlet-27156.herokuapp.com

以下是此Movie_Web app功能和特色介紹：


### 1.Single-Page Application：
  點擊任何連結，不會產生頁面重新載入，減少資料大量載入，增加使用者體驗。

### 2.註冊和登入：
  未登入訪客，只能進行瀏覽，需要註冊或登入，從server取得JSON web token後，才能進行post, put的動作。
  採用的是localStorage來保管token，一旦logout登出，即撤銷localStorage內的token。

### 3.分類篩選：
  左側列表有全種類(All genres)電影，也可以依照想要搜尋特定種類(genre)來顯示出電影。

### 4.分頁：
  每一分頁只顯示4個movie，超過換至下一個分頁。

### 5.搜尋：
  無論大小寫，可以輸入字母立即搜尋想要的電影標題。
  
### 6.排列：
  在table head標頭，點擊Tilte, Gernes, Stock, Rate，透過lodash可進行開頭字母A-Z升序排列，數字由小到大升序排列；再點擊一次，可以進行開頭字母和數字降序排列。

### 7.點擊喜歡：
  點擊電影右方的愛心圖形，立即被響應。

### 8.更新：
  登入使用者後，點進每個電影的標題，可進行更新電影標題、類別、存貨、評價。
  
### 9.新增：
  登入使用者後，可新增電影。

### 10.刪除：
  登入後的使用者，必須要有isAdmin=true，才有權限將電影清單進行刪除。
  
### 11.表單格式：
  使用Joi，當使用者沒有輸入好所需格式，例如：電影標題至少為5個字元以上，就會立即跳出紅框顯示，並無法按下submit按鈕，直到符合表單格式為止。

### 12.狀態提示：
  若成功更新或新增電影，toast會在頁面右上角跳出立即綠框成功資訊；若使用者發生操作錯誤，toast會在頁面右上角跳出紅框錯誤資訊。
  
### 13.非預期錯誤監測：
  使用Sentry.io來監測如果web app中使用者操作發生了error status不是在400~499之間，就會在Sentry.io被記錄起來，可以去檢查是使用者是哪   一段操作有問題。
  
### 14.reusable code：
  將使用的元件進行解耦分離放置common folder內，裡面的元件跟主題moive一點牽連都沒有，所以也可以直接拿被非當前主題moive元件繼承或是當作 子元件使用。
  
### 15.後端server:
  baseURL:https://obscure-atoll-21701.herokuapp.com
  以Node.js編程的server提供restuful api，而前端以axios進行HTTP methods：
  1./api/moives，提供給前端CRUD來操作電影的data。
  2./api/genres，提供前端get來取得genres data。
  3./api/users，提供前端post來進行使用者的註冊。
  4./api/auth，提供前端post來進行使用者的登入。
  
### 16.資料庫：
  後端將數據存放在Mongo Altas，有本地端和雲端的Mongo DB可進行存取。


