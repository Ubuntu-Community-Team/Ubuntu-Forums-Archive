---
title: "Problem reading pdf files"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by aam-aadmi on 2006-07-08
This might really be an easy problem to fix, but I am stuck: when using Mozilla Firefox, I am not able to read pdf files. When I click on any link that has a pdf file, I get a blank page! 

I have installed adobe along with the necessary (?) plug-ins; have re-started Firefox, but the problem persists. Any thoughts?

The following is what I have done:

sudo apt-get install acroread
sudo apt-get install mozilla-acroread
sudo apt-get install acroread-plugins

Thanks in advance.

---

### Post by someusernoob on 2006-07-08
I do not use acroread or any of those plugins. But the times i get a blank page in firefox is when something wants to be downloaded. Altough, when you set the file type to "auto-download' (edit > preferences > download > view & edit actions), it will automatic download the file without any notification to the default download folder. This leaves you behind with a blank page and no notification.

---

### Post by aam-aadmi on 2006-07-08
When I download that same file (if I can), save it on my disk and use Adobe reader to open it, the file opens! But there are cases, where I don't have the option to save the file; I have to read it from within my browser if I want to read it. That is when I get into problems.

---

### Post by Dr. Nick on 2006-07-08
why have you installed the acroread packages? Do you wat to be able to view pdf's in browser? 

I dont have any acroread packages installed. I havent done anything over the default install as far as pdfs are concerned. When I stumble upon a pdf link I am always asked to download it to HD or open from current location, if i hit open I think it uses evince in gnome, not sure what happens in KDE if thats what you use.

---

### Post by aam-aadmi on 2006-07-08
I installed all the acroread packages because I thought they would be useful for reading artilces in pdf formats in the web browser. For instance, the following is a weekly journal that I read regularly. Earlier, they used to have the articles in html format; but now they are using pdf formats for their articles:
[http://www.epw.org.in/showIndex.php](http://www.epw.org.in/showIndex.php)

Maybe, I am not getting something, but how do I read any article from the above webpage? I cannot even save them.

---

### Post by Dr. Nick on 2006-07-08
oh ok

yeah, with my configuration I cant read them either. Its the way they are embedded into the page i guess. So you would need a pdf plugin :(

---

### Post by aam-aadmi on 2006-07-08
Right, I also think that I need pdf plug-ins. And the ones that I have got (the acroread packages) don't seem to be working. Anybody has any ideas on how to deal with this situation.

---

### Post by catlett on 2006-07-08
I have no problem viewing those pdf's with the acroread plugins. Did you restart firefox after install? [IMG]http://i80.photobucket.com/albums/j180/brthomas503/pdffile.jpg[/IMG]



EDIT: WOW! That image link really puts up an image! I usually just attach a thumbnail but I wanted to try out Photobucket because I always had issues with image shack. Anyways I didn't realise the image would be like this. Sorry if it comes off as obnoxious, I just submitted without previewing.

---

### Post by aam-aadmi on 2006-07-08
That is strange; you seem to be able to read the articles where I cannot! Yes, I had re-started Firefox after install. Maybe, I should go ahead and re-start the computer once.

---

### Post by catlett on 2006-07-08
Restart maybe and for the heck of it, re-install with those commands again, maybe something didn't take right. It couldn't hurt.

---

### Post by aam-aadmi on 2006-07-08
Tried both: re-started the computer and also ran the three install commands again. Still, it does not work! Are you using KDE? I am using Gnome. IS it possible that this problem is specific to Gnome?

---

### Post by catlett on 2006-07-08
I am using Gnome. I have Ubuntu Dapper Drake 6.06

Let's check your firefox plkugins and make sure acroread is ther.

Open up firefox and clear the address bar. Then enter this ```
about:plugins
``` Then press the "go" button after the address bar. This will take you to your firefox plugin page. Check and see if Adobe RTeader is listed as the plugin for pdf's

---

### Post by Dr. Nick on 2006-07-08
I installed the plugins and it isnt listed, whats the filename displayed in about:plugins, Ill look for it on my hd and copy it to ff

---

### Post by catlett on 2006-07-08
I'm going to open up my firefox plugin folder and see what is in there as well, but this is a shot of my about:plugin page and what it says about adobe  
[IMG]http://i80.photobucket.com/albums/j180/brthomas503/aboutplugin.jpg[/IMG]

---

### Post by Dr. Nick on 2006-07-08
well 

nppdf.so appears no where on my hd....

wander why?

---

### Post by aam-aadmi on 2006-07-08
I typed "about:plugins" in the URL bar of Firefox; it shows exactly what was there in your screenshot! In particular, the file nppdf.so is shown to be there. And yet, I cannot read pdf files in the browser like you can. Strange!

---

### Post by aam-aadmi on 2006-07-09
I had been having problems with the adobe plug-in in Mozilla. Whenever I tried to read an embedded pdf file in Firefox, I would get a blank page. Though I had installed the acroread package and the plug-ins, it was still not working. 

A little more searching in this forum led me to a thread where this had been solved; I followed the advice and things now work. I thought I should write up the solution breifly, and here it is.

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

### Post by Audrey on 2008-03-05
Okay, I get pdf files in my email and can't read them.  What plug-ins are you talking about and are they on synaptic?

---

