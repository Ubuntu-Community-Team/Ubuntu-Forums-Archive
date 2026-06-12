---
title: "Reading embedded pdf in Firefox"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by aam-aadmi on 2006-07-09
I had been having problems with the adobe plug-in in Mozilla. Whenever I tried to read an embedded pdf file in Firefox, I would get a blank page. Though I had installed the acroread package and the plug-ins, it was still not working. 

A little more searching in this forum led me to a thread where this had been solved; I followed the advice and things now work. I thought I should write up the solution breifly (for future reference), and here it is.

Download and save the following:
[http://ardownload.adobe.com/pub/adobe/reader/unix/7x/7.0.5/enu/AdobeReader_enu-7.0.5-1.i386.tar.gz](http://ardownload.adobe.com/pub/adobe/reader/unix/7x/7.0.5/enu/AdobeReader_enu-7.0.5-1.i386.tar.gz)
(I saved it on my Desktop.)

Extract the files on the Desktop. You will be able to see a folder called AdobeReader.

Open AdobeReader, then open ILINX.TAR, then open Browser, then open Intelinux. You will see the following file: nppdf.so

Extract nppdf.so to the Desktop.

Now open the terminal and type the following command:
 sudo cp /home/username/Desktop/nppdf.so /usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so
(replace "username" with whatever is relevant for you in the first part of the above command)

Now re-start Firefox and you should be able to read embedded pdf files from within Firefox!

---

### Post by Dr. Nick on 2006-07-09
Hey I am glad you got this, however have you edited your origional thread with this solution, last I checked I didnt see it. May help to add at least a link to that thread incase someone finds it instead of this one,

Also you might consider posting in the HOWTO forum aswell.

I am off to try this as I still havent got it.

EDIT

Modified it a bit and got it working, I have a cusom version of firefox so your origional instructions may fix it for most.

Here is what I did

```
sudo cp /home/drnick/Desktop/nppdf.so /usr/lib/firefox/plugins/
sudo cp /home/drnick/Desktop/nppdf.so /opt/swiftfox/plugins/
``` 
The 2nd command is only needed if you have swiftfox. But your command plus them 2 and its working fine over here.

---

### Post by aam-aadmi on 2006-07-09
Yes, good idea. I will post on that thread too. 

Two more questions: (1) how do you get the "Code" to come in the box in a message? (2) How do you paste a screenshot in the text of your message?

---

### Post by Dr. Nick on 2006-07-09
To do both those easily switch to the advanced view "Go Advanced"

For Code
```
Type text and then mouse select it then hit the # key
```

Their is also a Insert Image button 2 left of the # for pics

---

### Post by aam-aadmi on 2006-07-09
Thanks. I am trying this out:
```

This will be in the box
``` 

This worked!

But, when I attempt to use the "insert image" button to include a screenshot, it asks for a URL. When I give the full path of the saved file (the screenshot), only the path shows up in the preview!

Ofcourse I could upload the file as an attachment, but that is not what I want. I want to include in the text of the message. 



Cheers!

---

### Post by Dr. Nick on 2006-07-09
Unless you use attachemts, To add a picture to a post using the insert image link will require you to upload the image to a site such as imageshack or another image host.

---

### Post by aam-aadmi on 2006-07-10
Ok. Now I get it. Thanks.

---

### Post by vasimakhtar on 2006-07-20
Hi,
Thanks. Perfect solution. I tried and it works.

cheers...........

---

