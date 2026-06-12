---
title: "Picasa web in Ubuntu"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by takakia on 2006-08-28
I find that there in no way to upload photo to picasa web using linux.  I am using a Kubuntu, and the picasaweb site doesn't mention a word about Linux in its help.  If anyone has a workaround pls help me.

---

### Post by awkward1234 on 2006-08-28
don't know about uploading pics in Picasa 2, but there is a special Linux verion of Picasa 2, with help section and everything, so hopefully what you want to know is on there somewhere:? 

[http://picasa.google.com/linux/](http://picasa.google.com/linux/)

---

### Post by takakia on 2006-08-29
thanks awkward.  But I am talking about picasaweb ([http://picasaweb.google.com](http://picasaweb.google.com)) . I want to upload to picasaweb for online storage/sharing.  But there seems to be no way to upload photos from a linux box.

---

### Post by eternalis on 2006-08-29
Well that site works for me. It shouldn't matter what OS you are using as it is a browser based app. It doesnt matter if they dont say anything about Linux in the Help, it works fine. Just make sure you have a Gmail account and it will work

---

### Post by xinix on 2006-08-29
Worked for me in firefox.  It took a while to upload but it did.

---

### Post by takakia on 2006-08-29
Thanks ! It works through browser. :D

---

### Post by egoldtech on 2006-08-30
Yes trought browser works is ok , 
but i think he is talking about a feature you can have on picasa for windows, when you have an account on picasawe, 
you can select a COMPLETE album,  hundreed hundreed of files, and just select "upload to web" , and continue .working ....
but there is not a version for linux, I have filled a suggestion already on Google.com , but may be some one knows how to put this windows wersion with wine????????

regards
Eze

---

### Post by egoldtech on 2006-09-03
Hi, install first Picasa 2 for linux from google .
[http://picasa.google.com/linux/](http://picasa.google.com/linux/)

then with Wine installed and all set up from this installation, I went to the special link they have to download Picasa Web album 2.5 beta version .exe
[http://picasa.google.com/download/index.html](http://picasa.google.com/download/index.html)

and then,  voila,  is working, I have picasa 2 working with this magic Buttons to upload my albums to the web .
only think the folder scanning dindt work well, I have to go to Add foolder
and  then select /home/xxx/Desktop to actually mak picasa scan my pics on my desktop .

hope they make a nice working package soon ..

regards
Eze

---

### Post by egoldtech on 2006-09-03
je, not is not working, whe I try to upload images to web album, i cannot login,  says:
Failed to conect to picasa web albums .


im stuck .

regards
eze

---

### Post by jmartinez on 2006-09-04
I am having an identical error message. PLEASE HELP! I love ubuntu, but having a funtional picasa is not an option for me...it is a must have.

---

### Post by egoldtech on 2007-06-15
PERFECT PICASA WEB ALBUMS AND UPLOADS:
m using Ubuntu Edgy on i386 and this is what I did to get it working:

1. I installed Picasa as usual (v2.2 for linux)
2. I started it up and scanned some folder containing photos
3. Shut down picasa AND the media detector
4. Instlled wine (apt-get install wine)
5. Downloaded picasa 2.5 for windows (wget
[http://dl.google.com/picasa/picasaweb-current-setup.exe](http://dl.google.com/picasa/picasaweb-current-setup.exe))
6. Installed it using wine (wine picasaweb-current-setup.exe)
7. When asked if I want to run Picasa, I did so, then I shut down
picasa AND the media detector (if running)
7. Moved the old picasa installation (as root):
    cd /opt/picasa/wine/drive_c/Program Files
    mv Picasa2 Picasa22
8. While in the same dir i copied the new installed Picasa 2.5:
    cp -R home/USERNAME/.wine/drive_c/Program\ Files/Picasa2/ .
8. Then it just worked... Good luck!
"

---

### Post by dankegel on 2008-03-03
You shouldn't need to do this anymore.
Picasa 2.7 for Linux should upload fine.
See [http://picasa.google.com/linux/download.html](http://picasa.google.com/linux/download.html)

There have been a few reports of people having
trouble downloading the 2.7 beta.   If this happens
to you, make sure you're using the current URL 
given on the above page.  And if that doesn't work,
please send a message to the Picasa on Linux forum,
[http://groups.google.com/group/Google-Labs-Picasa-for-Linux](http://groups.google.com/group/Google-Labs-Picasa-for-Linux).

Be sure to mention where you got the URL you're trying to download from...

---

