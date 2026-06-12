---
title: "Confused after downloading Fiesty .ISO"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2007-04-20
I'm currently using Dapper and have just downloaded FEISTY.

In the past, when downloding an .ISO file, I get 1 (sometimes 2 ) files on my desktop.

After downloading FEISTY I have 10 folders.

I'm not sure what to do next in order to burn a CD and would appreciate some help here, please.

---

### Post by Seisen on 2007-04-20
You need to burn just the .ISO at the lowest speed you can.

---

### Post by marko_4454 on 2007-04-20
> **L Campbell said:**
> I'm currently using Dapper and have just downloaded FEISTY.

In the past, when downloding an .ISO file, I get 1 (sometimes 2 ) files on my desktop.

After downloading FEISTY I have 10 folders.

I'm not sure what to do next in order to burn a CD and would appreciate some help here, please.

Are you looking at what the .iso file has INSIDE?
Dont do that....just burn the .iso

---

### Post by L Campbell on 2007-04-20
> **marko_4454 said:**
> Are you looking at what the .iso file has INSIDE?
Dont do that....just burn the .iso

Thanks for your interest.

Yes, I guess I'm looking at what is inside.  It arrived on my desktop as a 'window', [ubuntu-7.04-desktop-i386.iso] with an option on it to 'extract'.  

I clicked on extract and then got an additional 8 files.

Why would it not arrive as just 1 .iso file?

Is there some way I can 'back out' and get to an .iso file?

---

### Post by lluisanunez on 2007-04-20
You still must have the .iso file... just delete the others!

---

### Post by L Campbell on 2007-04-20
> **lluisanunez said:**
> You still must have the .iso file... just delete the others!

Thanks.

I'm sure you are correct but this is what I am seeing:-

Hopefull my screenshot will show up here.

---

### Post by marko_4454 on 2007-04-20
> **L Campbell said:**
> Thanks.

I'm sure you are correct but this is what I am seeing:-

Hopefull my screenshot will show up here.

Yea, thats INSIDE the .iso file. Close that window and you know that in order to get the screenshot you show, you need to double click some icon right? THATS the .iso
Just get out of what you are showing in the screen and look for the iso. Do NOT double click it, just right click it and there should be a "burn to CD" or something like that. Click that and burn it.
if there is no "burn to CD" option then reply here....

---

### Post by raazman on 2007-04-20
Ya, don't extract the files. You will need to burn the actual iso file (1 file with the .iso) onto a cd using a program that burns an iso. remember to choose "burn iso" or something similar.

---

### Post by kpkeerthi on 2007-04-20
I think you double-clicked the .iso file? Did you? Thats why the archive manager is displaying its contents. Right-click on the .iso file and select **Burn to Disk**

---

### Post by L Campbell on 2007-04-20
> **marko_4454 said:**
> Yea, thats INSIDE the .iso file. Close that window and you know that in order to get the screenshot you show, you need to double click some icon right? THATS the .iso
Just get out of what you are showing in the screen and look for the iso. Do NOT double click it, just right click it and there should be a "burn to CD" or something like that. Click that and burn it.
if there is no "burn to CD" option then reply here....

Thanks.

I guess the problem is that I DIDN'T have to clck on anything to get the screenshot.  I made the screenshot from what I received. When I look in 'places' > 'recent documents' there is only one file related to FEISTY and it is the one which is the screenshot.

Maybe I should try the download again, from another location and see if I get the proper looking file?

---

### Post by n3tfury on 2007-04-20
> **L Campbell said:**
> Thanks.

I guess the problem is that I DIDN'T have to clck on anything to get the screenshot.  I made the screenshot from what I received. When I look in 'places' > 'recent documents' there is only one file related to FEISTY and it is the one which is the screenshot.

Maybe I should try the download again, from another location and see if I get the proper looking file?

the others are correct.  you opened the .iso and now it's displaying its contents.  look again or do a search with ".iso" parameters in the folder you download to.  

if you still can't find it, download again, but this time, make sure it's on your desktop so you won't lose it.

---

### Post by L Campbell on 2007-04-21
> **n3tfury said:**
> the others are correct.  you opened the .iso and now it's displaying its contents.  look again or do a search with ".iso" parameters in the folder you download to.  

if you still can't find it, download again, but this time, make sure it's on your desktop so you won't lose it.

OK, I have downloaded it again (from another location) but I still get the same thing:-


I ABSOLUTELY didn't 'open' it, despite the fact that logic would dictate that this is what I must have done.  All I did was click on 'download' and accepted the default.  Nothing else but it arrives on my desktop 'open'.

Couls a fault in my computer cause this?

Thanks for your patience.

---

### Post by MiCovran on 2007-04-21
OK, I think i can see the problem. After you clicked on the download button in your browser, you have chosen to open the file instead of saving it to disk.

---

### Post by L Campbell on 2007-04-21
> **n3tfury said:**
> the others are correct.  you opened the .iso and now it's displaying its contents.  look again or do a search with ".iso" parameters in the folder you download to.  

if you still can't find it, download again, but this time, make sure it's on your desktop so you won't lose it.

OK, I have downloaded it again (from another location) but I still get the same thing:-

My screenshot should show up here but the 'Manage Attachments' section tells me that my screen shot is too large of a file.  That would be the same file that it accepted yesterday in my previous post.

If it wasn't for bad luck, I wouldn't be having ANY luck today.    :-)


I ABSOLUTELY didn't 'open' it, despite the fact that logic would dictate that this is what I must have done.  All I did was click on 'download' and accepted the default.  Nothing else but it arrives on my desktop 'open'.

Could a fault in my computer cause this?

Thanks for your patience.

---

### Post by L Campbell on 2007-04-21
> **MiCovran said:**
> OK, I think i can see the problem. After you clicked on the download button in your browser, you have chosen to open the file instead of saving it to disk.

Thank you, this is in fact what I did, so I am downloading it again.

I appreciate the help.

Please ignore my post #14.

---

### Post by trippinnik on 2007-04-21
Check the /temp folder, you probably have a few .iso files in there now.  What is the default download directory for your web browser?  Is the browser set to automatically open .iso files?  
but actually you could start with this in the terminal:

sudo updatedb
locate feisty

then you'll get the path, go there with nautilus or your burning app and burn th iso.

---

