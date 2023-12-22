# گزارش آزمایش هفتم درس مهندسی نرم افزار

## اعضای گروه

+ سید محمدمهدی حاتمی 98109561
+ پیمان حاجی محمد 98170776

## شرح آزمایش 
ابتدا مانند آزمایش های قبلی مخزن گیت پروژه را راه اندازی کرده و تنظیمات محافظت از برنچ main را روی آن اعمال می کنیم. 

### بخش اول :‌ بررسی پوشش آزمون در json-simple 
برای بخش اول ابتدا پروژه‌ی json-simple را با Intellij باز می کنیم. سپس اجرای تست با پوشش آزمون را اجرا می کنیم. در اجرای اول به خطایی بر می‌خوریم که با اعمال توصیه ی Intellij و تغییر ورژن در یکی از وابستگی‌ها، برطرف می‌شود. 

![Screenshot from 2023-12-17 23-34-35](https://github.com/smmhatami/SE-Lab7/assets/62210297/57308ba0-4726-496d-923b-7df7fdad77f0)

در عکس زیر نتیجه را مشاهده می کنید. 

![Screenshot from 2023-12-17 23-38-38](https://github.com/smmhatami/SE-Lab7/assets/62210297/e7298e0c-9fa3-4847-b7b9-90e5bfbffb47)

در ادامه مطابق با دستور آزمایش خروجی html گزارش پوشش آزمون را نیز دریافت کرده و بررسی می کنیم. 

![Screenshot from 2023-12-17 23-40-08](https://github.com/smmhatami/SE-Lab7/assets/62210297/3cc5eff0-810e-4c08-866e-f0125c8a1483)

![Screenshot from 2023-12-17 23-41-02](https://github.com/smmhatami/SE-Lab7/assets/62210297/57d9c28a-6477-493b-9f5e-2b22a8ceddbd)

### بخش دوم : بهبود پوشش آزمون در CodeCoverageProject 
برای این بخش نیز ابتدا پروژه را باز کرده و اجرای تست با پوشش آزمون را بر روی تمام تست های آن اجرا می کنیم. به این منظور روی پوشه ی test/java کلیک راست کرده و گزینه ی Run 'All Tests' with Coverage را انتخاب می کنیم. نتیجه ی این اجرا را در تصویر زیر مشاهده می کنید. 

![Screenshot from 2023-12-18 00-13-04](https://github.com/smmhatami/SE-Lab7/assets/62210297/98dce122-69d1-49fc-8420-1fb563da664d)

سپس کدهایی به تست اضافه شده و پوشش آمزون به این صورت افزایش پیدا کرد. 
![Screenshot from 2023-12-22 17-18-07](https://github.com/smmhatami/SE-Lab7/assets/62210297/cbd5c629-3e71-46db-b3f7-926ea27862f1)

در ادامه نحوه ی آزمون شدن هر یک از کلاس ها را به اختصار توضیح می دهیم. 

- کلاس BehaviorException : این Exception که توسط هر دو تابع کلاس TrafficBehaviorServiceImpl پرتاب می شود، در سه تست نوشته شده در کلاس TrafficBehaviorServiceTest با فراخوانی این توابع پرتاب شده و تست می شود.
- کلاس PersonException : این کلاس دو نوع پرتاب Exception دارد که یکی از آن ها یک خطا دارد و دیگری لیستی از خطاها. حالت تک خطای این تابع در تابع delete کلاس PersonServiceImpl استفاده شده است که در فرایند تست کردن حذف از تست های ما فراخوانی شده است و حالت چند خطای آن در PersonValidator استفاده شده است که در تابع insert از PersonServiceImpl استفاده شده است که به صورت متعدد در تست های پیاده سازی شده ی ما فراخوانی شده است. 
- کلاس PersonValidator : این کلاس صحت سنجی نمونه های validator را به عهده دارد و به همین منظور در کلاس PersonServiceImpl به دفعات استفاده شده است. هنگامی که توابع insert، delete از این کلاس فراخوانی می شوند، این توابع تست می شوند.

- کلاس FootPassenger : این کلاس یک عابر پیاده را پیاده سازی می کند. تمام توابع این کلاس به غیر از setCrossedTheCrosswalk و crossedTheCrosswalk تست شده بودند. برای کامل شدن تست این کلاس در تابع testFootpassengerCrossTheStreet_shouldThrowBehaviorExceptionWhenFootpassengerCrossesTheRoadDuringHeavyTrafficAndWhileTheTrafficLightIsRed بید تابع setCrossedTheCrosswalk را نیز فراخوانی کنیم تا تعریف کردن عابر پیاده ی ما کامل شده باشد.

![Screenshot from 2023-12-22 18-11-32](https://github.com/smmhatami/SE-Lab7/assets/62210297/33c91fd4-5a22-4566-a9dc-5ef34ae7532d)

- کلاس Gender : این کلاس که جنسیت افراد را مشخص می کند، از ابتدا هنگامی که میخواستیم یک فرد جدید تعریف کنیم تست شده بود.
- کلاس Person : این کلاس یک فرد را نمایندگی می کند. تمام توابع این کلاس به جز getAge تست شده بودند. به منظور کامل شدن پوشش و تست شدن این تابع، در تابع تست testInsert_shouldInsertPersonWithSuccessWhenAllPersonsInfoIsFilledAndPersonIsNotChanged بعد از تمام شدن عملیات درج جدول، بررسی می کنیم که فیلدهای person داده شده تغییر نکرده باشند.

![Screenshot from 2023-12-22 18-14-44](https://github.com/smmhatami/SE-Lab7/assets/62210297/31b54d8a-17f6-4ead-81c1-9e050fb13550)

- کلاس StreetDirectionFlow : این یک enum بوده که یک طرفه یا دو طرفه بودن یک خیابان را مشخص می کند. با set کردن این ویژگی برای یک خیابان در تست هایمان این کلاس نیز کاور می شود.
- کلاس Traffic : این کلاس مدل ترافیکی ما را مشخص می کند که به کمک متد های setter آن میتوان وضعیت ترافیکی و سرعت مجاز را در آن تعیین کرد. در تست هایمان تمامی متد های این کلاس به جز متد های getter پوشش داده شده اند.
- کلاس TrafficLight : این کلاس که تنها وضعیت چراغ راهنمایی رانندگی را نگهداری می کند، از ابتدا در تست های مختلف کلاس TrafficBehaviorServiceTest و هنگام تعریف یک موجودیت ترافیک جدید استفاده و تست شده بود.
- کلاس PersonRepository : این کلاس در واقع تست شده و استفاده شده است ولی در پوشش های Intellij نمایش داده نمی شود. تمام توابع این کلاس در PersonServiceImpl فراخوانی و استفاده شده اند و با افزایش پوشش این فایل که توضیح داده میشود، پوشش آزمون برای این کلاس هم بالا رفته و کامل شده است.
- کلاس PersonServiceImpl : از این کلاس متد های delete و get تست نشده بودند که با فراخوانی آنها، پس از ایجاد یک person آن متد ها به همراه تعدادی exception دیگر تست شدند.

![image](https://github.com/smmhatami/SE-Lab7/assets/61017890/9427cf30-22b1-44b3-92a4-0386afde32de)
![image](https://github.com/smmhatami/SE-Lab7/assets/61017890/30290965-d20d-4fd8-b1b5-6044b78f3ddc)

- کلاس TrafficBehaviorServiceImpl :‌ این کلاس از ابتدا به صورت کامل تست شده بود. این کلاس دو تابع دارد که هر دو در تست های TrafficBehaviorServiceTest فراخوانی شده اند. 
