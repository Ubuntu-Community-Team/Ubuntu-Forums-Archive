---
title: "How do you change the MIME type of a file"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by pclark99 on 2007-04-29
How do you change the MIME type of a file?

 I have saved the settings of my Terminal Server Client session (via TS's Save) to a file on my desktop. But if I double click the file, Xfce thinks it is a text file, since the MIME type is text/plain. If I right click the file and tell Xfce to "Open with Another Application" and select Terminal Server Client the double clicking works fine since TSC is now the default application to open now. Problem is now every text file I open (via double click), Xfce opens it with TSC instead of a text editor. So, how to a change the MIME type of the TSC settings file so that TSC is opened.

I am using xubuntu 6.06 wih the Xfce desktop.

Thanks for your help.

---

### Post by kidders on 2007-05-01
Hi there,

Your question is a little confusing. :-( You can't change what type of file something is. For instance, if something is a PNG image, it's a PNG image ... there is no way to change that.

---

### Post by pclark99 on 2007-05-02
What I am saying is that I use Terminal Server (TS) to connect to my other computer which is an XPWin machine. In TS, I select the protocol as RDPv5 with the IP address to my XPWin machine. To prevent from having to type in this infomation every time I start TS I clicked the "Save As" button under the "General" tab. This created a .rdp file.

Problem is, if I double click this file it opens it in my text editor instead of in TS. In other words it does not recognize the file type as being of TS origin. Yes it is a text file my nature but it is used to open a TS session. 

If I right click the file and select TS as the file to open it with. Xfce remembers this and then tries to open all text files with TS. Which is not what I want. I want just the .rdp file to be opened using TS and text files to be open with my editor. Its a pain if I have to keep using the right mouse button all the time to select the proper program to run the file on.

I thought by changing the MIME type of the .rdp file, this would tell Xfce that .rdp files are to be opened with TS.

---

### Post by stefe on 2007-07-09
try searching for "MIME  default application" - there are a number of threads that way

basically, you have to create a MIME file - these are found in either 
/usr/share/MIME
or $/.local.share

then re-update associations with 
sudo update-mime-database /usr/share/mime
sudo dpkg-reconfigure shared-mime-info
killall gnome-panel
killall nautilus

Hope this helps

Stephen

---

### Post by kamahl on 2007-12-06
These instructions don't seem to work for me.  I have a .desktop file, however it has a x-thunar/suspected-malware for the MIME.  How do I change this back to the normal desktop shortcut?  It will not launch unless I change the MIME back to normal.

---

### Post by AndrewTheArt on 2008-07-03
Try - 

```
sudo -i
echo "application/x-rdp rdp" >> /etc/mime.types
```

[http://andrewtheart.blogspot.com/2008/07/fixing-rdp-mime-type-in-ubuntu-linux.html](http://andrewtheart.blogspot.com/2008/07/fixing-rdp-mime-type-in-ubuntu-linux.html)

---

