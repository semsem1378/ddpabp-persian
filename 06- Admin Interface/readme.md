<div dir='rtl'>
<h1>فصل ۶ - رابط کاربری ادمین</h1>
در این بخش، موضوعات زیر را بررسی خواهیم کرد:

* شخصی سازی بخش ادمین
* بهینه سازی مدل ها در قسمت ادمین
* عرف و تنظیمات متداول برای ادمین
* تغییر ویژگی ها

ویژگی برجسته جنگو، رابط کاربری ادمین است،که برگ برنده آن در رقابت است. این بخش یک برنامه داخلی(built-in) بوده که به صورت خودکار یک رابط کاربری را برای افزودن یا ویرایش محتوای وبسایت، تولید می کند.برای خیلی از کاربران،بخش ادمین یک برنامه نجات دهنده است؛ که عملیات خسته کننده ی ساخت یک رابط کاربری برای ادمین و مدل های داخل پروژه را به دوش می کشد.

بخش ادمین این امکان را برای تیم شما فراهم می کند که به صورت همزمان محتوا را افزوده و توسعه کد را ادامه دهید. زمانی که مدل های شما آماده باشند و انتقال آن ها(migrations) صورت گیرد، تنها نیاز است تا یک یا دو خط کد به برنامه افزوده شود تا مدل شما به رابط کاربری ادمین اضافه گردد. نحوه انجام این عملیات را در ادامه خواهیم دید.

### استفاده از رابط کاربری ادمین

در یک پروژه ی جدید، رابط کاربری ادمین به صورت پیش فرض فعال شده است. پس از راه اندازی سرور توسعه برنامه، شما می توانید یک صفحه ورود به رابط ادمین را در آدرس  http://127.0.0.1:8000/admin مشاهده کنید.

اگر مشخصات ادمین سایت را(superuser) تعریف کرده باشید( یا مشخصات هر کاربر دیگر - شامل نام کاربری و رمز عبور و...)، می توانید همانطور که در تصویر دیده می شود، به رابط ادمین وارد شوید.

![رابط کاربری ادمین در جنگو برای یک پروژه جدید](https://raw.githubusercontent.com/ftg-iran/ddpabp-persian/main/06-%20Admin%20Interface/images/image-000.png "اسکرین شات از رابط کاربری ادمین در جنگو برای یک پروژه جدید")

تصویری از رابط کاربری ادمین در جنگو برای یک پروژه جدید

اگر قبلا از جنگو استفاده کرده اید،متوجه خواهید شد که ظاهر رابط ادمین بهتر از قبل شده است، بخصوص آیکن های svg در صفحه های نمایش با دی پی آی بالا(high-DPI).

گرچه مدل های شما در حال حاضر قابل مشاهده نیست، مگر آن که مدل ها را از طریق بخش ادمین ثبت کنید. بخش ادمین در برنامه شما در فایل admin.py در دسترس است. برای مثال، در مسیر sightings/admin.py، مدلی به نام Sighting را به شکل زیر ثبت کرده ایم:
    ‍‍
> <p dir='ltr'>from django.contrib import admin from . import models
> <br>
>  admin.site.register(models.Sighting)
> </p>

اولین آرگومان تابع register کلاس مدل را برای افزودن به بخش ادمین سایت مشخص می کند. در اینجا، آرگومان دوم تابع register؛ که مدل کلاس ادمین بوده، حذف شده است. بنابراین رابط کاربری که به صورت پیش فرض تعریف شده است را خواهیم داشت. در ادامه خواهیم دید که چطور می توانیم مدل ادمین خود را شخصی سازی کنیم.

###  فانوس دریایی 

"داری قهوه میخوری؟" صدایی در گوشه ی ابدارخانه پرسید.«سو» نزدیک بود که قهوه اش را بریزد. مردی قد بلند که لباس قرمز و آبی پوشیده بود ایستاد و دست به کمر، لبخندی زد. نشانی که بر سینه او نقش بسته بود؛ به حروف بزرگ نوشته بود،کاپیتان آبویس (capitan obvious).

سو در حالی که لکه قهوه را پاک میکرد گفت "خدای من!".

کاپیتان گفت "ببخشید که ترسوندمت، چه مورد اضطراری پیش اومده؟"

زنی آرام از بالا گفت: "مشخص نیست که خودش هم نمیدونه؟"

سو؛ سایه ای که به آرامی از سالن رو باز به پایین می آمد را دنبال می کرد. بخشی از صورت زن به وسیله موهای مشکی اش پوشیده شده بود.

کاپیتان گفت:"سلام هکسا" سپس ادامه داد،"آخرش پیام سایت کمیک چی بود؟"

اندکی بعد، همه آن ها در دفتر کار «استیو»، در حالی که به مانیتور او نگاه میکردند؛ جمع شدند.
«ایوان» گفت: "میبینی! گفته بودم که هیچ فانوسی در صفحه ی اصلی سایت نیست. ما هنوز داریم روی این ویژگی کار می کنیم."

استیو گفت: "صبر کن، بذار با یک اکانت غیرپرسنلی وارد بشم".

طی چند ثانیه، صفحه سایت تازه سازی شد و فانوس قرمز به طور برجسته ای در بالای صفحه سایت قرار گرفته بود.
کاپیتان فریاد زد:"خودشه! همون فانوسی که بهت گفته بودم".

استیو گفت:"یک لحظه صبر کن!". او سورس فایلی که برای ویژگی های جدید سایت ثبت شده بود را بررسی کرد. با یک نگاه به ویژگی های فانوس متوجه شد که چه چیزی اشتباه شده است.

> <p dir='ltr'>
>  if switch_is_active(request, 'beacon') and not request.user.is_staff():
>  <br>
>  beacon.activate()
> </p>

استیو گفت:"ببخشید، یه خطای منطقی اتفاق افتاده.بجای اینکه این ویژگی را فقط برای پرسنل فعال کنم، ناخواسته آن را برای کسانی که جز پرسنل نبودند فعال کردم.حالا درست شد. بابت این اشفتگی عذر میخوام".

کاپیتان با یک نگاه تاسف بار پرسید:"پس هیچ مورد اضطراری وجود نداشت؟". هکسا با آرنج به بازوی او زد و گفت:"فکر نکنم کاپیتان!"
سپس صدای مهیبی آمد. همه به سمت راهرو دویدند. ظاهرا مردی از طریق یکی از دیوارهای شیشه ای کف تا سقف، وارد اتاق شده بود. در حالی که تکه های شکسته شیشه را در دستش تکان میداد؛ ایستاد و گفت: "ببخشید،با نهایت سرعت خودم رو رسوندم،دیر رسیدم؟".
هکسا خندید و گفت: "نه «بیلتز» منتظرت بودیم که برسی".

بهینه سازی مدل ها برای بخش ادمین:

در اینجا مثالی موجود است که مدل ادمین را برای کارایی و جلوه ای بهتر، بهینه سازی کرده است. می توانید به تفاوت های میان دو اسکرین شات زیر نگاهی بیاندازید تا ببینید که چطور چند خط کد، می تواند انقدر تفاوت ایجاد کند.

![حالت پیش فرض نمایش لیستی در بخش ادمین](https://raw.githubusercontent.com/ftg-iran/ddpabp-persian/main/06-%20Admin%20Interface/images/image-001.png)

حالت پیش فرض نمایش لیستی بخش ادمین، برای مدل sightings

پس از آن که روش توضیح داده شده برای شخصی سازی بخش ادمین پیاده سازی شود، همان اطلاعات مشابه با دسترسی آسان تر و بهتری به شکل زیر نمایش داده می شوند:

![نمایش لیستی بهینه شده در بخش ادمین](https://raw.githubusercontent.com/ftg-iran/ddpabp-persian/main/06-%20Admin%20Interface/images/image-002.png)

نمایش لیستی بهینه شده بخش ادمین برای مدل sightings

برنامه ادمین به اندازه کافی هوشمند است که موارد زیادی را از مدل شما به صورت خودکار درک و دریافت کند. اگرچه گاهی اطلاعات اشاره شده قابل بهبود است. این عمل معمولا به صورت اضافه کردن یک ویژگی یا یک متد به مدل خودتان(بجای مدل ادمین) انجام می شود.

در اینجا کد مربوط به مدل بهینه شده ی sightings را داریم:

<pre dir='ltr' style='background-color:#D3D3D3'>\# <span class="pl-s1">models</span>.<span class="pl-s1">py</span>
<span class="pl-k">class</span> <span class="pl-v">Sighting</span>(<span class="pl-s1">models</span>.<span class="pl-v">Model</span>):
    <span class="pl-s1">superhero</span> <span class="pl-c1">=</span> <span class="pl-s1">models</span>.<span class="pl-v">ForeignKey</span>(
        <span class="pl-s1">settings</span>.<span class="pl-v">AUTH_USER_MODEL</span>, <span class="pl-s1">on_delete</span><span class="pl-c1">=</span><span class="pl-s1">models</span>.<span class="pl-v">CASCADE</span>)
    <span class="pl-s1">power</span> <span class="pl-c1">=</span> <span class="pl-s1">models</span>.<span class="pl-v">CharField</span>(<span class="pl-s1">max_length</span><span class="pl-c1">=</span><span class="pl-c1">100</span>)
    <span class="pl-s1">location</span> <span class="pl-c1">=</span> <span class="pl-s1">models</span>.<span class="pl-v">ForeignKey</span>(<span class="pl-v">Location</span>, <span class="pl-s1">on_delete</span><span class="pl-c1">=</span><span class="pl-s1">models</span>.<span class="pl-v">CASCADE</span>)
    <span class="pl-s1">sighted_on</span> <span class="pl-c1">=</span> <span class="pl-s1">models</span>.<span class="pl-v">DateTimeField</span>()

    <span class="pl-k">def</span> <span class="pl-en">__str__</span>(<span class="pl-s1">self</span>):
        <span class="pl-k">return</span> <span class="pl-s">"{}'s power {} sighted at: {} on {}"</span>.<span class="pl-en">format</span>(
            <span class="pl-s1">self</span>.<span class="pl-s1">superhero</span>,
            <span class="pl-s1">self</span>.<span class="pl-s1">power</span>,
            <span class="pl-s1">self</span>.<span class="pl-s1">location</span>.<span class="pl-s1">country</span>,
            <span class="pl-s1">self</span>.<span class="pl-s1">sighted_on</span>)

    <span class="pl-k">def</span> <span class="pl-en">get_absolute_url</span>(<span class="pl-s1">self</span>):
        <span class="pl-k">from</span> <span class="pl-s1">django</span>.<span class="pl-s1">urls</span> <span class="pl-k">import</span> <span class="pl-s1">reverse</span>
        <span class="pl-k">return</span> <span class="pl-en">reverse</span>(<span class="pl-s">'sighting_details'</span>, <span class="pl-s1">kwargs</span><span class="pl-c1">=</span>{<span class="pl-s">'pk'</span>: <span class="pl-s1">self</span>.<span class="pl-s1">id</span>})

    <span class="pl-k">class</span> <span class="pl-v">Meta</span>:
      <span class="pl-s1">unique_together</span> <span class="pl-c1">=</span> (<span class="pl-s">"superhero"</span>, <span class="pl-s">"power"</span>)
      <span class="pl-s1">ordering</span> <span class="pl-c1">=</span> [<span class="pl-s">"-sighted_on"</span>]
      <span class="pl-s1">verbose_name</span> <span class="pl-c1">=</span> <span class="pl-s">"Sighting &amp; Encounter"</span>
      <span class="pl-s1">verbose_name_plural</span> <span class="pl-c1">=</span> <span class="pl-s">"Sightings &amp; Encounters"</span>
</pre>

حال نحوه استفاده ادمین از این ویژگی ها را بررسی می کنیم:

<h4>()__str__:</h4>
بدون این متد، عناوین فلیدهای مدل شما به صورتی کسالت بار و ناخوانا نمایش داده می شوند. تمام فیلدها با فرمتی به شکل <Sighting:Sighting object> نمایش داده می شوند. سعی کنید که تمام ویژگی های منحصر به فرد آبجکت را در نمایش str(یا در نمایش Unicode برای پایتون ورژن ۲)، همچون نام آبجکت و ورژن آن؛ نمایش دهید. هر آنچه که به نمایش بدون ابهام آبجکت در ادمین کمک کند، کاربردی است.

#### ()get_absolute_url:
این متد برای جابجا شدن بین صفحه سایت ادمین و نمایش جزئیات آبجکت متناظر روی سایت شما(صفحه اصلی) کارآمد است.اگر این متد تعریف شده باشد، یک دکمه با عنوان "نمایش بر روی سایت" در کنج بالا و دست راست صفحه ی ویرایش آبجکت در داخل ادمین؛ نشان داده می شود

#### ordering:
- مرتب سازی: بدون این گزینه ی متا،ورودی های شما با ترتیبی که از دیتابیس دریافت می شوند،نمایش داده می شوند. همانطور که تصور می کنید، اگر تعداد زیادی آبجکت داشته باشید؛ این شیوه مرتب کردن برای ادمین سایت جالب نخواهد بود. به طور معمول، ادمین ها ترجیح می دهند که ورودی های جدیدتر را در ابتدا مشاهده کنند؛ بنابراین مرتب سازی با ترتیب زمانی معکوس(با نشان منفی) رایج است.


-   verbose_name:
اگر این ویژگی را حذف کنید، نام مدل شما از حالت کمل کیس با حروف اول بزرگ، به حالت ساده تبدیل می شود.در این مثال، از این ویژگی به صورت بیهوده و برای تبدیل Sighting به Sighting & Encounter استفاده شده است.
اما بعضی مواقع اسمی که به صورت خودکار برای مدل ساخته می شود، گیج کننده است؛ پس شما می توانید نامی که برای کاربر خوانا باشد را برای نمایش در بخش ادمین تعیین کنید.

 
- verbose_name_plural
مجددا، حذف این ویژگی نتایج جالبی خواهد داشت. از آنجا که جنگو برای اسامی مدل ها حرف جمع s را در انتها می آورد، لغت جمع به صورت"Sighting & Encounters"(در صفحه ادمین و نه جای دیگر)نمایش داده می شود. پس بهتر است با استفاده از این ویژگی، شکل صحیح آن را تعریف کنیم.

پیشنهاد می شود که تگ متا مذکور را نه تنها برای رابط ادمین، بلکه برای نمایش بهتر در قسمت های شل و فایل های لاگ نیز، تعریف کنید.اگرچه، شما می توانید از ویژگی های بسیار بیشتر ادمین برای شخصی سازی کلاس مدل ادمین بهره ببرید. در این مثال، شخصی سازی را به صورت زیر انجام می دهیم:

`# admin.py`

<pre dir='ltr' style='background-color:#D3D3D3'><span class="pl-k">class</span> <span class="pl-v">SightingAdmin</span>(<span class="pl-s1">admin</span>.<span class="pl-v">ModelAdmin</span>):
    <span class="pl-s1">list_display</span> <span class="pl-c1">=</span> (<span class="pl-s">'superhero'</span>, <span class="pl-s">'power'</span>, <span class="pl-s">'location'</span>, <span class="pl-s">'sighted_on'</span>)
    <span class="pl-s1">date_hierarchy</span> <span class="pl-c1">=</span> <span class="pl-s">'sighted_on'</span>
    <span class="pl-s1">search_fields</span> <span class="pl-c1">=</span> [<span class="pl-s">'superhero'</span>]
    <span class="pl-s1">ordering</span> <span class="pl-c1">=</span> [<span class="pl-s">'superhero'</span>]
<span class="pl-s1">admin</span>.<span class="pl-s1">site</span>.<span class="pl-en">register</span>(<span class="pl-s1">models</span>.<span class="pl-v">Sighting</span>, <span class="pl-v">SightingAdmin</span>)</pre>

بگذارید تا به این ویژگی ها نگاهی دقیق تر داشته باشیم.


- list_display
این گزینه نمونه های ساخته شده ازمدل را به صورت جدولی نشان می دهد. بجای استفاده از \__str__ این گزینه تمام فیلدهای ذکر شده را به صورت ستونی قابل مرتب سازی نشان می دهد. این قابلیت برای مرتب سازی مدل با بیش از یک ویژگی ، ایده آل است.


- date_hierarchy:
تعیین هر فیلد تاریخ-زمان با این ویژگی، یک توضیح دقیق تر برای هر تاریخ ارائه خواهد داد.( به سال های قابل کلیک در زیر کادر جستجو توجه کنید)

- search_fields
این گزینه یک کادر جستجو بالای لیست ایجاد می کند. هر عبارتی که جستجو شود در فیلدهای مشخص شده جستجو خواهد شد. بنابراین فقط فیلدهای کاراکتری و فیلدهای متنی می توانند در اینجا استفاده شوند.

- ordering:
این گزینه به ترتیب پیش فرض مدل شما تقدم می یابد. این مورد زمانی کاربردی است که شما نیاز به ترتیب نمایش متفاوتی در صفحه ادمین دارید؛ که در اینجاترجیحا اعمال شده است.

ما فقط زیرمجموعه ای از پر استفاده ترین ویژگی های ادمین را ذکر کردیم. نوع خاصی از وبسایت ها، استفاده زیادی از رابط ادمین دارند؛در این موارد، شدیدا توصیه می شود که به مستندات جنگو مراجعه و بخش مربوط به ادمین را مطالعه کنید.

#### هر کسی نباید ادمین باشه

از آنجا که سلخت رابط ادمین بسیار آسان است، ممکن است که افراد به غلط از آن استفاده کنند. برخی با فعال کردن تیک staff(کارکنان) برای کاربران، به صورت بی رویه به آن ها دسترسی برای مدیریت این بخش می دهند.


متاسفانه، این چیزی نیست که رابط ادمین برای آن ساخته شده. همانطور که از معنی لغت staff پیدا است، ابزاری داخلی است برای کارکنان تا محتوا را وارد کنند. این یک ابزار فعال در محیط تولید است(زمانی که سایت بر روی سرور اپلود شده)، اما برای کاربران نهایی وبسایت شما در نظر گرفته نشده است.


بهتر است از رابط ادمین برای وارد کردن دیتا های ساده استفاده شود. برای مثال،در یک پروژه ی اینترانت در سطح یک مدرسه مشاهده کردم، هر یک از معلم ها به عنوان یک ادمین برای اپ جنگو در نظر گرفته شده بود. این تصمیم اشتباهی بود چرا که محیط کاربری ادمین، معلمان را گیج می کرد.


گردش کار برای برنامه ریزی کلاس  شامل بررسی برنامه های معلمان و دانش آموزان دیگر است. استفاده از رابط ادمین به آن ها دید مستقیمی از پایگاه داده می دهد. کنترل بسیار کمی بر نحوه تغییر داده ها توسط مدیر وجود دارد.


بنابراین، تعداد افرادی که به رابط ادمین دسترسی دارند را در حداقل ممکن نگه دارید. در اعمال تغییرات از طریق رابط ادمین زیاده روی نکنید، مگر اینکه وارد کردن یک داده ساده باشد، مثل اضافه کردن محتوای یک مقاله.


#### الگوهای سرآمد: 

`به کاربران نهایی دسترسی به رابط ادمین ندهید.
`

مطمئن شوید که تمام مدیران سایت شما از تناقض هایی که ممکن است در داده ها از طریق رابط ادمین ایجاد شود، آگاه هستند.اگر ممکن است به صورت دستی تغییرات را ذخیره کنید؛یا از برنامه هایی مثل django-audit-log، که می تواند گزارش تغییرات اعمال شده در قسمت ادمین رابرای ارجاع در آینده ذخیره کند، استفاده کنید.

در یک نمونه مثال از یک دانشگاه، ما یک رابط کاربری مجزا برای اساتید ساختیم، همانند یک رابط برنامه ریزی دوره ها. چنین ابزاری حاوی برنامه ای است که می تواند برای مقاصدی بسیار فراتر از عملکرد ورودی های داده در رابط ادمین باشد؛ مثل شناسایی تناقض بین تاریخ دوره ها.



اساسا، اصلاح اشکالات رابط ادمین مستلزم ایجاد ابزار های توانمندتری برای یک مجموعه مشخص از کاربران است. با این حال، مسیر آسان(و اشتباه) اعطای دسترسی مدیریت به آنها را انتخاب نکنید.


#### سفارشی سازی رابط مدیریت

رابط مدیریت خارج از چهارچوب هنگام شروع کار بسیار مفید است. متاسفانه، اکثریت افراد تصور می کنند که تغییر دادن رابط مدیریت جنگو بسیار مشکل است و آن را به همان شکلی که هست رها می کنند. در وافع رابط مدیریت جنگو قابلیت شخصی سازی فوق العاده ای دارد و ظاهر آن را می توان با حداقل تلاش، شدیدا تغییر داد.


#### تغییر عنوان


بسیاری از کاربران رابط مدیریت ممکن است با عنوان مدیریت جنگو (django administration) دچار مشکل شوند. احتمالا بهتر باشد که این مورد را به عبارتی اختصاصی تغییر دهید؛ له عنوان مثال، "مدیر سایت من"، یا عبارت جالب توجهی چون "محیط مهرمانه superbook".

ایجاد این تغییرات بسیار راح است، فقط لازم است تا خط کذ زیر را به صفحه urls.py سایت خود اضافه کنید.

<pre dir='ltr' style='background-color:#D3D3D3'><span class="pl-s1">admin</span>.<span class="pl-s1">site</span>.<span class="pl-s1">site_header</span> <span class="pl-c1">=</span> <span class="pl-s">"SuperBook Secret Area"</span></pre>

#### تغییر پایه و شیوه نامه

تقریبا هر صفحه مدیریتی، از یک الگوی پایه مشترک توسعه یافته است که به آن admin/base_site.html می گویند.

این بدان معنی است که شما با یک دانش حداقلی از html و css، می توانید به دلخواه ظاهر و حالت رابط کاربری ادمین را تغییر دهید.

یک فایل با نام ادمین در مسیری که الگوهایتان قرار دارد بسازید. سپس محتوای فایل base_site.html را از سورس کد جنگو کپی کرده و در فایل جدید، به دلخواه آن را ویرایش کنید. اگر نمی دانید که الگوها(templates) کجا قرار گرفته اند،کافی است که کد زیر را در شل جنگو اجرا نمایید.

<p dir='ltr' style='background-color:#ADD8E6'>
from os.path import join
<br>
from django.contrib import admin
<br>
print(join(admin.\__path__[0], "templates", "admin")) /home/arun/env/sbenv/lib/python3.6/site- packages/django/contrib/admin/templates/admin
</p>

اخرین خط، محل قرارگیری تمام فایل های الگوی ادمین شما است.شما می توانید هر کدام از این فایل ها را تغییر و یا تعمیم دهید.

برای مثال در تغییر پایه الگوی ادمین، شما می توانیدفونت تمام قسمت ادمین را به فونت Special Elite تغییر دهید.

برای این کار لازم است که محتویات فایل  base_site.html را از مسیر الگوهای ادمین به مسیر admin/base_site.html؛ در یک پوشه از الگوهای خودتان، کپی کنید. سپس کد زیر را به انتهای آن اضافه کنید.

<pre dir='ltr' style='background-color:#D3D3D3'>{% block extrastyle %}

<span class="pl-kos">&lt;</span><span class="pl-ent">link</span>
  <span class="pl-c1">href</span>="<span class="pl-s">http://fonts.googleapis.com/css?family=Special+Elite</span>"
  <span class="pl-c1">rel</span>="<span class="pl-s">stylesheet</span>"
  <span class="pl-c1">type</span>="<span class="pl-s">text/css</span>"
/&gt;

<span class="pl-kos">&lt;</span><span class="pl-ent">style</span> <span class="pl-c1">type</span>="<span class="pl-s">text/css</span>"<span class="pl-kos">&gt;</span>
  <span class="pl-ent">body</span><span class="pl-kos">,</span>
  <span class="pl-ent">td</span><span class="pl-kos">,</span>
  <span class="pl-ent">th</span><span class="pl-kos">,</span>
  <span class="pl-ent">input</span> {
    <span class="pl-c1">font-family</span><span class="pl-kos">:</span> <span class="pl-s">"Special Elite"</span><span class="pl-kos">,</span> cursive;
  }
<span class="pl-kos">&lt;/</span><span class="pl-ent">style</span><span class="pl-kos">&gt;</span>
{% endblock %}</pre>


این کد شیوه نامه جدیدی برای تغییر فونت مربوطه می افزاید که به تمام صفحات ادمین اعمال می شود.


اضافه کردن یک ویرایشگر متن غنی(rich-text) برای ویرایش WYSIWYG


گاهی اوقات نیاز دارید که کد جاوااسکریپتی در بخش ادمین داشته باشید. یک نیاز مشترک، استفاده از یک ویرایشگر HTML است؛ مثل CKEditor، برای فیلدهای متنی شما.

راه های متعددی برای پیاده سازی این موضوع در جنگو وجود دارد، برای مثال، استفاده از کلاس داخلی Media در کلاس مدل ادمین(ModelAdmin).با این حال، من تعمیم الگوی change_form در ادمین را مناسب ترین روش تشخیص دادم.

برای مثال، اگر شما یک برنامه به اسم پست ها دارید، لازم است که فایلی با نام change_form.html در مسیر templates/admin/posts/ بسازید. اگر نیاز دارید که ویرایشگر CKEditor ( یا هر ویرایشگر جاوااسکریپت، اما این ویرایشگر مورد ترجیح من است)برای فیلد پیام یک مدل از این برنامه نمایش داده شود، محتوای فایل مربوطه می تواند به صورت زیر باشد:

<pre dir='ltr' style='background-color:#D3D3D3'>{% extends "admin/change\_form.html" %} {% block footer %} {{ block.super }}

<span class="pl-kos">&lt;</span><span class="pl-ent">script</span> <span class="pl-c1">src</span>="<span class="pl-s">//cdn.ckeditor.com/4.4.4/standard/ckeditor.js</span>"<span class="pl-kos">&gt;</span><span class="pl-kos">&lt;/</span><span class="pl-ent">script</span><span class="pl-kos">&gt;</span>
<span class="pl-kos">&lt;</span><span class="pl-ent">script</span><span class="pl-kos">&gt;</span>
  <span class="pl-c1">CKEDITOR</span><span class="pl-kos">.</span><span class="pl-en">replace</span><span class="pl-kos">(</span><span class="pl-s">"**id_message**"</span><span class="pl-kos">,</span> <span class="pl-kos">{</span>
    <span class="pl-c1">toolbar</span>: <span class="pl-kos">[</span><span class="pl-kos">[</span><span class="pl-s">"Bold"</span><span class="pl-kos">,</span> <span class="pl-s">"Italic"</span><span class="pl-kos">,</span> <span class="pl-s">"-"</span><span class="pl-kos">,</span> <span class="pl-s">"NumberedList"</span><span class="pl-kos">,</span> <span class="pl-s">"BulletedList"</span><span class="pl-kos">]</span><span class="pl-kos">]</span><span class="pl-kos">,</span>
    <span class="pl-c1">width</span>: <span class="pl-c1">600</span><span class="pl-kos">,</span>
  <span class="pl-kos">}</span><span class="pl-kos">)</span><span class="pl-kos">;</span>
<span class="pl-kos">&lt;/</span><span class="pl-ent">script</span><span class="pl-kos">&gt;</span>
<span class="pl-kos">&lt;</span><span class="pl-ent">style</span> <span class="pl-c1">type</span>="<span class="pl-s">text/css</span>"<span class="pl-kos">&gt;</span>
  .<span class="pl-c1">cke</span> {
    <span class="pl-c1">clear</span><span class="pl-kos">:</span> both;
  }
<span class="pl-kos">&lt;/</span><span class="pl-ent">style</span><span class="pl-kos">&gt;</span>

{% endblock %}</pre>

قسمتی که بولد شده، شناسه ساخته شده به صورت خودکار برای المان فرمی است که می خواهیم از یک کادر متنی ساده به یک ویرایشگر متن غنی تبدیل کنیم. این تغییر سایر کادرهای متنی فیلدهای سایت ادمین را تحت تاثیر قرار نمی دهد. این اسکریپت ها به بلوک انتهایی (footer) افزوده شده، پس المان های فرم در DOM قبل از آن که تغییر کنند،ساخته شده اند.

شیوه های دیگر دستیابی به این موضوع ممکن است نیازمند نصب برنامه ها و تنظیمات دیگری باشد. برای تغییر فقط یک صفحه از سایت ادمین، این زیاده روی است. شیوه قبلی به شما این انعطاف پذیری را می دهد که بین ویرایشگر جاوااسکریپت یا موارد دلخواه خودتان، انتخاب کنید.


#### ادمین با تم بوت استرپ

جای تعجب نیست که یک درخواست برای سفارشی سازی بخش ادمین این است که آیا می توان بوت استرپ را با آن ادغام کرد یا خیر. بسته های(pacakges) زیادی هستند که می توانند این کار را انجام دهند؛ همانند Django-admin-bootstrapped  و یا Django suit.

بجای این که تمام الگوهای ادمین را خودتان تغییر دهید، این بسته ها تم های آماده به مصرفی را فراهم کرده اند.نصب و بارگذاری این تم ها آسان است. از آنجا که بر اساس بوت استرپ هستند، واکنشگرا(responsive) بوده و با مولفه ها و ویجت های متنوعی همراه هستند.



#### بازسازی کامل 

تلاش های زیادی برای دوباره به تصویر کشیدن بخش ادمین انجام شده است.  Grappelli یک پوسته محبوب است که رابط ادمین جنگو را با با ویژگی های جدیدی تعمیم می دهد؛ همانند جستجوهای پیشنهاد دهنده(autocomplete lookups) و خطوط تاشو(collapsible inlines). با استفاده از ابزار  django-admin-tools شما یک داشبورد و نوار منو با قابلیت سفارشی سازی خواهید داشت.



تلاش هایی برای بازنویسی مجدد رابط ادمین صورت گرفته، نظیر django-admin2  و nexus؛ که پیشرفت قابل توجهی نداشتند. همچنین یک ابزار رسمی به نام AdminNext برای اصلاح کامل رابط ادمین ساخته شد.
با در نظر گرفتن حجم، پیچیدگی و محبوبیت رابط ادمین موجود؛ هر تلاشی از این قبیل زمان بسیار زیادی خواهد برد.

#### حفاظت از ادمین

رابط ادمین سایت شما تقریبا به هر داده ای که در سایت ذخیره شده است دسترسی دارد،بنابراین دروازه این مخزن اطلاعات را بدون محافظ رها نکنید.در واقع یک نشانه که گویای این است که شخص از جنگو استفاده می کند،این است که وقتی به صفحه http://example.com/admin/ می روید، یک صفحه آبی برای ورود به بخش می بینید.

زمانی که سایت را بر روی سرور بالا می آورید، بهتر است که مسیر ادمین را به مسیری که کمتر مشخص باشد تغییر دهید. انجام این کار با سادگی با کد زیر در فایل urls.py انجام می شود.

<pre dir='ltr' style='background-color:#D3D3D3'><span class="pl-en">path</span>(<span class="pl-s">'secretarea/'</span>, <span class="pl-s1">admin</span>.<span class="pl-s1">site</span>.<span class="pl-s1">urls</span>),</pre>

راهکاری که مقداری پیچیده تر است آن است که یک صفحه ادمین فیک (رد گم کن!) در مسیر پیش فرض داشته باشید.(بسته ی django-admin-honeypot package را جستجو کنید).
با این حال بهترین راه حل استفاده از HTTPS در محیط ادمین(و هر جای دیگر از وبسایت) است.چرا که استفاده از HTTP ساده، موجب ارسال تمام داده ها به صورت یک متن ساده در شبکه می شود.


مستندات سرور وبسایت خود را در رابطه با نحوه ی تنظیم HTTPS برای درخواست های ادمین (یا اگر ممکن است، تمام وبسایتتان) بررسی کنید. بر روی Nginx، انجام این کار ساده است؛ که شامل تعیین محل گواهی SSL می شود. در نهایت،تمامی درخواست های HTTP دریافت شده برای ادمین را به صفحات HTTPS بازنشانی کنید، تا خیال راحت تری داشته باشید!

الگوی زیر تنها محدود به بخش رابط ادمین نیست، اما با این وجود در این فصل گنجانده شده؛ زیرا اغلب در این بخش کنترل می شود.

#### پرچم های(flags) الگو - ویژگی

مشکل: انتشار ویژگی های جدید برای کاربران باید مستقل از بارگذاری کد متناظر در تولید باشد.

راه حل: استفاده از پرچم های ویژگی برای فعال یا غیر فعال کردن ویژگی ها پس از بارگذاری به صورت انتخابی.

##### شرح مشکل

امروزه رفع مشکلات مکرر و مدیریت ویژگی های جدید در حین فعال بودن سایت بر روی سرور، مسئله ای رایج است.بسیاری از این تغییرات توسط کاربران مورد توجه قرار نمی گیرد. اگرچه ویژگی های جدیدی که تاثیر قابل توجی از نظر عملکرد و قابلیت های سایت دارند، باید به صورت مرحله ای عرضه شوند. به عبارت دیگر، بارگذاری باید از مرحله انتشار و فعال سازی جدا شود.

یک فرآیند ساده انتشار نسخه جدید، ویژگی های تازه را به محض بارگذاری شدن آن ها بر روی سایت، فعال می کند. این امر به طور بالفوه می تواند نتایج فاجعه باری داشته باشد؛ از مشکلات کابران ( پر شدن منابع پشتیبانی و نرم افزاری شما) تا مشکلات عملکردی(خرابی و غیرفعال شدن سایت).


از این رو در سایت های بزرگ، جداسازی فرآیند بارگذاری بروزرسانی جدید در زمان تولید و فعال سازی آن ها؛ اهمیت زیادی دارد. حتی گاهی پس از فعال سازی ممکن است فقط برای عده خاصی از کاربران آن را قابل مشاهده کنیم. این گروه منتخب می توانند کارکنان یا مجموعه محدودی از مشتریان باشند که پیش نمایش اولیه را دریافت می کنند.

##### شرح راه حل:

بسیاری از سایت ها فعال سازی ویژگی های جدید را با استفاده از پرچم های ویژگی کنترل می کنند.به طور معمول این یک سوئیچ است که در هر مرحله کنترل می شود."فلیپر" سوئیچی در کد شما است که تعیین می کند آیا یک ویژگی باید در دسترس مشتریان خاص قرار گیرد یا خیر. اما ما در اینجا عبارت عام پرچم ویژگی(feature flag) را به کار می بریم.

پکیج های جنگو دارای پرچم های ویژگی مانند gargoyle و django-waffle هستند. این پکیج ها پرچم های سایت را در پایگاه داده ذخیره می کنند.آنها را می توان از طریق رابط ادمین یا از طریق دستورات مدیریت فعال یا غیرفعال کرد. از این رو هر محیطی(تولید،آزمایش،توسعه و ...) می تواند مجموعه ای از ویژگی های فعال شده خود را داشته باشد.

پرچم های ویژگی در اصل در سایت فلیکر ثبت شده بودند.(ادرس http://code.flickr.net/2009/12/02/flipping-out را بررسی کنید). آنها یک منبع کد را بدون هیچ شاخه ای مدیریت کردند- یعنی همه چیز در شاخه اصلی بررسی شد. آنها همچنین این کد را چندین بار در روز وارد محیط تولید کردند. اگر آنها متوجه می شدند که یک ویژگی جدید باعث خرابی چیزی در محیط تولید شده است یا بارگذاری روی پایگاه داده را افزایش داده است؛ به سادگی آن را با استفاده از پرچم ویژگی، غیر فعال می کردند.

پرچم های ویژگی می توانند برای موقعیت های دیگری نیز استفاده شوند(مثال زیر از Django Waffle استفاده می کند):

##### آزمایش:
یک پرچم ویژگی می تواند برای کاربران خاصی فعال باشد. این کاربران می توانند کارکنان شما و یا برخی پذیرندگان اولیه باشند که مورد هدف شما هستند؛ که به  صورت زیر مشاهده می کنید:

<pre dir='ltr' style='background-color:#D3D3D3'><span class="pl-k">def</span> <span class="pl-s1">my_view</span>(<span class="pl-s1">request</span>):
    <span class="pl-k">if</span> <span class="pl-en">flag_is_active</span>(<span class="pl-s1">request</span>, <span class="pl-s">'flag_name'</span>):
    \#<span class="pl-v">Behavior</span> <span class="pl-k">if</span> <span class="pl-s1">flag</span> <span class="pl-c1">is</span> <span class="pl-s1">active</span>.</pre>

سایت ها می توانند چندین آزمایش از این دست را به صورت همزمان و موازی اجرا کنند، بنابراین مجموعه های مختلف کاربران ممکن است تجربیات متفاوتی داشته باشند. کمیت ها و بازخوردهای این آزمایش های کنترل شده،قبل از انتشار در سطح وسیع تر؛ جمع آوری و بررسی می شوند.


##### آزمایش A/B:

این آزمایش نیز مشابه با مورد پیشین است، با این تفاوت که کاربران به صورت تصادفی در یک ازمایش کنترل شده انتخاب می شوند. این روش در طراحی وبسایت بسیار مرسوم است و با این هدف تعیین آن که کدام تغییرات موجب افزایش نرخ تبدیل می شود، انجام می شوند. در ادامه مثالی از آن را میبینیم:

<pre dir='ltr' style='background-color:#D3D3D3'><span class="pl-k">def</span> <span class="pl-s1">my_view</span>(<span class="pl-s1">request</span>):
    <span class="pl-k">if</span> <span class="pl-en">sample_is_active</span>(<span class="pl-s1">request</span>, <span class="pl-s">'new_design'</span>):
    \#<span class="pl-v">Behavior</span> <span class="pl-s1">for</span> <span class="pl-s1">test</span> <span class="pl-s1">sample</span>.</pre>

##### تست عملکرد:
گاهی اوقات اندازه گیری تاثیر یک ویژگی بر عملکرد سرور دشوار است. در چنین شرایطی بهتر است از ابتدا پرچم را فقط برای درصد کمی از کابران فعال کنید. اگر عملکرد آن مورد رضایت بود، درصد فعال سازی را می توان به تدریج افزایش داد.

##### محدودیت های خارجی:
همچنین می توانیم از پرچم های ویژگی به عنوان سوئیچ ویژگی در سراسر سایت استفاده کنیم که در دسترس بودن آن خدمات را منعکس می کند. به عنوان مثال، از کار افتادن سرویس های خارجی مانند Amazon S3 می تواند باعث شود که کابران در حین انجام اقداماتی مانند آپلود تصویر، با پیام های خطا مواجه شوند. هنگامی که سرویس خارجی برای مدت طولانی خاموش است، یک پرچم ویژگی را می توان فعال مرد و دکمه آپلود را غیر فعال کرد و یا پیامی قابل فهم در خصوص زمان خرابی سرویس نشان داد. این ویژگی ساده در وقت کاربر صرفه جویی کرده و تجربه کاربری بهتری را ارائه می دهد:

<pre dir='ltr' style='background-color:#D3D3D3'><span class="pl-k">def</span> <span class="pl-en">my_view</span>(<span class="pl-s1">request</span>):
    <span class="pl-k">if</span> <span class="pl-en">switch_is_active</span>(<span class="pl-s">'s3_down'</span>):
    \#<span class="pl-v">Disable</span> <span class="pl-s1">uploads</span> <span class="pl-c1">and</span> <span class="pl-s1">show</span> <span class="pl-s1">it</span> <span class="pl-c1">is</span> <span class="pl-s1">downtime</span></pre>

عیب اصلی این روش آن است که کد با عبارت های شرطی شلوغ می شود. با این حال، این مسئله را می توان با پاکسازی و تصحیح دوره ای کدها و حذف شروط برای ویژگی هایی که کاملا تایید شده اند ، یا حذف ویژگی هایی که به طور دائمی غیرفعال شده؛ تا حدی برطرف کنید.

فعال سازی پرچم ها را می توان از سایت مدیریت با ساتفاده از سیستم های احراز هویت و مجوزهای کاربر داخلی کنترل کرد. همچنین می توانید درصد کاربران نمونه برای ازمایش را از رابط مدیریت کنترل کنید.


### خلاصه

در این فصل، برنامه مدیریت داخلی جنگو(ادمین) را بررسی کردیم. نه تنها این بخش به عنوان یک ابزار کمکی بسیار مفید است، بلکه می توان برای بهبود ظاهر و کارایی، آن را سفارشی سازی کرد.

در فصل بعدی با در نظر گرفتن الگوهای مختلف و موارد استفاده شده متداول، نگاهی به نحوه استفاده موثرتر از فرم ها در جنگو خواهیم داشت.

</div>





















