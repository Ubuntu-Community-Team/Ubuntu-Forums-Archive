---
title: "Uploading Webpages Help!!"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by louise81 on 2008-01-18
Hi,

I have started a new website, and had it working ok last night. I have since done something ,that is not allowing my pages to link to eachother. All of the pages except one [http://www.scoobylous.com.au/price-list.html](http://www.scoobylous.com.au/price-list.html) allow me to click onto other pages, however, once I click on this page it won't let me get anywhere.

Does someone know what I need to do to change this?

Cheers 
Lou from Sydney!:confused:

---

### Post by smartalecks on 2008-01-18
why are the files linked to file:///C:/file.html? You don't need to make them the absolute paths if the files are in the same folder as the file that the links are on...

---

### Post by lluisanunez on 2008-01-18
You should check the code, links in your page all start with C:/ instead of http://
What program are you using to write them?
And what OS? :-)

---

### Post by jan quark on 2008-01-18
I do not see any links like < a href="bla bla.html"> in your source of the webpage.

Did you make the page with an WYSIWYG editor ?

Pages made with tables are not very userfriendly. The best are written in html+ css.

---

### Post by unclejac on 2008-01-18
When you look at the price list page most of your pages links still refer to your C drive location. Which is fine for writing your HTML in an offline state. 

Once loaded up onto the web each of your pages links need to refer to the actual address on the web. 

You did it fine for the other pages: 

look at the source code for the price-list.html page 

This part:

```
 <a href="file:///C:/index.html"> 
```

Should be:

```
<a href="http://www.scoobylous.com.au/index.html">
```

 etc. 

Sort the code on the whole page for each of the links to the other pages and and upload the page again to your website and you should be back in business.

---

### Post by louise81 on 2008-01-18
Thanks for your reply 

I don't know how to make them c:// all of these html's are saved in ftp desktop - the program I am using.

---

### Post by unclejac on 2008-01-18
What did you use to create the web pages ?

---

### Post by unclejac on 2008-01-18
This is the line to change right at the end off the price-list.html page 

```
<map name="Map" id="Map"><area shape="poly" 
coords="38,269,41,257,44,241,52,220,60,205,68,190,77,179,85,170,96,160,106,155,116,152,124,152,136,157,146,166,158,176,167,188,175,199,183,209,191,226,196,241,198,260,196,275,191,284,180,290,168,292,140,284,127,280,116,283,104,287,90,289,76,291,60,291,51,287,44,281"
 href=**"file:///C:/index.html"**><area shape="poly" coords="36,269" href="#"><area 
shape="poly" coords="72,4,95,6" href="#"><area shape="poly" 
coords="72,9,98,11,113,31,122,69,116,107,99,119,76,106,60,65,60,33" 
href=**"file:///C:/price-list.html"**><area shape="poly" 
coords="6,102,5,148,28,183,53,185,65,165,62,120,42,93,20,88" 
href=**"file:///C:/our-services.html"**><area shape="poly" 
coords="157,123,135,96,140,45,161,14,178,10,195,30,197,72,185,106,170,121" 
href="**file:///C:/our-policies.html"**><area shape="poly" 
coords="196,205,182,171,191,128,216,107,238,116,246,157,230,195,215,204" 
href=**"file:///C:/contact-us.html"**>

	
```

---

### Post by louise81 on 2008-01-18
thanks very much for your help!!:)

---

### Post by unclejac on 2008-01-18
I think you did it ??? :D

Well done!

---

### Post by louise81 on 2008-01-18
it only took me 4 ever!!

thanks!! much appreciated!!

---

### Post by unclejac on 2008-01-18
oh one last thing. 

The link on this image "logo.jpg" on your price-list.html page still needs changing.

[IMG]http://img85.imageshack.us/img85/322/42668452yi5.jpg[/IMG]

The code on the page to change is near the top, in the table body:

```
<font face="Times New Roman"><a href=**"file:///C:/index.html"**><img src="images/logo.jpg" alt="SCOOBY LOU’S PET CARE THAT COMES TO YOU!" border="0" height="122" width="119"></a></font></td>
```

):P

---

