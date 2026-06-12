---
title: "flash 9"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by IrishGangsta on 2006-07-18
Is there a flash player 9 yet for linux?

---

### Post by Sef on 2006-07-18
> Is there a flash player 9 yet for linux?

No, there is not.  It is expected to be released in early 2007 according to Adobe.

[Flash 9]("http://weblogs.macromedia.com/emmy/archives/2006/05/yes_virginia_th.cfm")

---

### Post by lazyd2 on 2006-07-18
> **Sef said:**
> No, there is not.  It is expected to be released in early 2007 according to Adobe.

[Flash 9]("http://weblogs.macromedia.com/emmy/archives/2006/05/yes_virginia_th.cfm")
Thanks for the info

---

### Post by Sef on 2006-07-18
You're welcome.  If you have any questions, please post them.

---

### Post by OU812 on 2006-07-18
You mean for web pages? Here's a link

[http://www.adobe.com/products/acrobat/readstep2.html](http://www.adobe.com/products/acrobat/readstep2.html)

I got this installed on my vector machine, haven't tried it yet on ubuntu. If this is not what you meant, my bad.

john

P.S. You'll have to install it from source.

---

### Post by deusdeceptor on 2006-07-20
I think he meant flash 9 not adobe acrobat ;)

---

### Post by Klemik on 2006-07-20
Is there flash 8 ? Every time I go to macromedia download page I can download only version 7 and cant see some flashes that require version 8 :(

---

### Post by Uncle Spellbinder on 2006-07-20
> **Klemik said:**
> Is there flash 8 ? Every time I go to macromedia download page I can download only version 7 and cant see some flashes that require version 8 :(

Flash 8 will not be available for Linux. There have been several posts regarding this in these forums. We'll have to wait for Flash 9 in early '07.

---

### Post by OU812 on 2006-07-20
Sorry, I got the link wrong. To get the correct link, when you go to a page that has flash animation, a bar at the top of the browser has a button with a msg like install plugins. Hit this button. You will go through a series of steps to install flashplayer that will fail since flashplayer thinks you're using win. At the end of this process a button appears: manual install. Follow this link to a linux .tar.gz file. Download. At the terminal do

tar xzvf install_flash_player_7_linux.tar.gz
cd install_flash_player_7_linux
./flashplayer-installer

and follow the prompts.

john

P.S. I just did these steps a few minutes ago so it should work.

---

### Post by GStubbs43 on 2006-07-20
Isn't that for Flash Player 7, not 9, some sites require newer versions of flash and you can't view them on Ubuntu.

---

### Post by mattisking on 2006-07-20
Flash 7 is the only available Linux version from Macromedia/Adobe. Flash 8 has no Linux version. Flash 8.5 was originally supposed to support Linux but then 8.5 was dumped (for everyone) for 9.0. While Flash 9 has come out for Windows users, it will not be available for Linux until early next year. You can follow the blog of it's development here: [http://blogs.adobe.com/penguin.swf/]("http://blogs.adobe.com/penguin.swf/")

---

