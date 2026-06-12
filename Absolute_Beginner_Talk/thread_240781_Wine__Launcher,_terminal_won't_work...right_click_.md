---
title: "Wine:  Launcher, terminal won't work...right click open with &quot;Wine&quot; will"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by Cornbreadly on 2006-08-21
I'm using xubuntu.  I want to access the Youtube amd G-Video clips, and I have failed at getting audio through the fixes posted here.  I decided to go the wine route but I can't get a launcher or terminal to successfully launch firefox.  But  a right click and open with "wine" will launch it no prob.  What is the command that gets it going and do I just use that same command in the launcher?

I have a dual boot with XP(trying to leve it behind totally) so i just copied over my firefox install from over there and put it in the .wine/c_drive/

I dont know if that makes a difference or not.

I appreciate the help.

---

### Post by Kilz on 2006-08-21
> **Cornbreadly said:**
> I'm using xubuntu.  I want to access the Youtube amd G-Video clips, and I have failed at getting audio through the fixes posted here.  I decided to go the wine route but I can't get a launcher or terminal to successfully launch firefox.  But  a right click and open with "wine" will launch it no prob.  What is the command that gets it going and do I just use that same command in the launcher?

I have a dual boot with XP(trying to leve it behind totally) so i just copied over my firefox install from over there and put it in the .wine/c_drive/

I dont know if that makes a difference or not.

I appreciate the help.

You arew going to have to edit this a little, useing your username.

```
wine "/home/YourUserName/.wine/c_drive/Program Files/Mozilla Firefox/firefox.exe"

```

---

### Post by H.E. Pennypacker on 2006-08-21
I strongly recommend against using your Windows Firefox copy through Wine.  Instead, use what is available for Linux natively.  You can still copy over all the bookmarks and settings using the native Firefox installation without using Wine.

The Wine command to start an application is *wine application-name*.  If you enter that into the terminal, Wine will start an application.  The same is true for creating a launcher.

To create a Wine launcher, see the Wine entry on Ubuntu Wiki.  I added info on doing this, but they're Gnome instructions.

---

### Post by Cornbreadly on 2006-08-21
Ok, I got it to work with adding the quotation marks.  I hate missing simple things like that.

Anyways, H.E.P., why do you advise against using the firefox install from windows?  If my meager understanding of linux talk is working, I already have a native install of firefox for my ubuntu.  I use it constantly, like for instance, to type this.  I plan to use the windows version to view the flash 9 sites like youtube.  My daughter is addicted to the 2 choreographed OK GO videos.  everyone seems to have a problem getting those sites to work under ubuntu until adobe gets around to releasing a version for linux.

Am I corrupting something, like my windows Dll's?

PS who is the chick in your avatar?

---

### Post by Kilz on 2006-08-21
I think everyone will advise against using any browser with wine. The problems isn't using it on a few sites because you need functionality. The problem is some people will think its ok to use it all the time. In this case its a defiant security risk. Then they think, wow Firefox works good let me try IE, then use it all the time. That is a disaster waiting to happen.

---

### Post by H.E. Pennypacker on 2006-08-22
> Anyways, H.E.P., why do you advise against using the firefox install from windows?

Linux exists, not so much to provide a free alternative to Windows, but as an advancement of goals the open source community believes in.  We promote open source software, and less use of Wine is recommended in order to strengthen what *we've* created.  Using a Windows version of Firefox supports that Windows version.  If something's wrong with the Linux version, it should be made better, so that we can improve Linux software instead of encouraging the use of Windows software.

Furthermore, using a Windows version of Firefox through Wine is not necessary.  Some people have had a success getting Flash 9 (or 8) websites through one method or another.  

Also, if you have no other option left, use Internet Explorer through Wine.  It allows Wine developers to focus on strengthening one application (Internet Explorer on Wine) instead of two (Firefox and IE).

If your daughter wants to use Disney, someone did come up with a way of circumventing their restrictions.  Check out this thread:

[http://ubuntuforums.org/showthread.php?t=236413](http://ubuntuforums.org/showthread.php?t=236413)

YouTube doesn't use Flash 9.  I don't do anything special (no Wine), and I can view YouTube videos.  You should have no problems using YouTube.  

The girl in my avatar is Meagan Good.  Beautiful, yes, I know.

---

