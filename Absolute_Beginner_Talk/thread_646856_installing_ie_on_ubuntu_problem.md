---
title: "installing ie on ubuntu problem"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by Falc7 on 2007-12-21
I am trying to install IE for linux, i have done everything it says on this page
[http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu](http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu)

But the screen goes unresponsive when it is trying to 'download everything we need' on item IE_S2.CAB. I've tried it several times and it just dosen't work

What can i do? Any other way to install IE on Ubuntu?

---

### Post by spiderbatdad on 2007-12-21
do you have wine?

---

### Post by Falc7 on 2007-12-22
yep, i had wine before i did everything in that step by step guide

---

### Post by SOULRiDER on 2007-12-22
Do you actually _NEED_ IE or you justd otn like firefox? There are other alternatives to Firefox, my advice is, dont use IE unless you really really really need it.

---

### Post by Joeb454 on 2007-12-22
What reason do you have for IE?

Like soulrider said, and I believe like the official website says - it has only been ported to allow for testing of websites from Linux systems.

If you need it for that we'll try and help, if you just don't like firefox try [opera]("http://www.opera.com")

---

### Post by Falc7 on 2007-12-28
Firefox is great, I would rather not use IE, But there are some Chinese websites which are only avaliable in IE.
Some pages related to taobao, and qq zone.

---

### Post by adityakavoor on 2007-12-28
try IE4linux

[guide]("http://www.tatanka.com.br/ies4linux/page/Main_Page")

---

### Post by LinuxIsInnovation on 2007-12-28
You can try ie4linux:
[http://www.tatanka.com.br/ies4linux/news/](http://www.tatanka.com.br/ies4linux/news/)

For installing the old ie6:
[http://aranea.zuavra.net/index.php/54/](http://aranea.zuavra.net/index.php/54/)

IE7 installation is a bit complicated..

---

### Post by adityakavoor on 2007-12-28
opera does what ie can do

---

### Post by freddybob on 2007-12-28
Have you tried the Chinese websites with Firefox and the [User Agent Switcher]("https://addons.mozilla.org/en-US/firefox/addon/59") extension?

---

### Post by shuttleworthwannabe on 2007-12-28
I have IE installed through wine (needed it for some wine applications); as far as I can see it is not a 100% functional. keeps hanging and does not render pages as in true-blue IE in windows. Just my experience,
 
S

---

### Post by Falc7 on 2007-12-28
I have tried getting ie4linux, but like i said, the screen goes unresponsive halfway through downloading everything.

I have instaleld the user agent switcher extension now, but i can't see any menu to change to ie mode. I can see the user agent switcher extension in tools. But nothing that lets me change a tab to ie or anything. What should i do to change to ie?

thanks for the help btw guys

---

### Post by freddybob on 2007-12-29
The User Agent tools menu item should give you a [submenu like this]("http://chrispederick.com/work/user-agent-switcher/") which will allow you to choose browser type.

I should explain, this simply changes how Firefox identifies itself on websites not how it renders the pages.  Sometimes this is enough to get you into a site that claims to only works in IE.

---

### Post by (((X))) on 2007-12-29
konqueror browser can act like IE.
Open konqueror->tools->change browser identification-> internet explorer

---

### Post by rkd on 2007-12-29
I haven't tried ie4linux, so I'm just speculating on things here. I could easily be wrong, so you'll have to decide whether to try this.

From your description, it seems like it downloaded several things before getting stuck. I'm not clear on exactly how it got stuck. When you say the screen goes unresponsive, do you mean the whole system stops and you have to turn power off and reboot? Or do you mean the window doing the download just sits there, apparently doing nothing? 

I'll assume the latter. Could it be that the IE_S2.CAB file it is downloading is just very large and takes a very long time to download? Perhaps you could look in the directory where it is putting the files being downloaded to see whether the file size is slowly increasing. 

From looking at the install scripts, it seems that it tries to show download progress by putting a progress bar on the screen (I'm looking at the non-gui install script). Do you see that progress bar for IE_S2.CAB? Does it grow in size for a while, then stop growing or does it never start?

Have you tried asking it to install Internet Explorer 5.5 instead of Internet Explorer 6? Maybe that would be more successful.

---

### Post by jslmg on 2008-01-02
The whole point of using IE in Linux or Mac is that we need it to access websites that require the Active X plugin. That's all.

In Korea, China and Japan, MOST websites require the Active X plugin. Just a fact of life over here. I need it to use my university's web portal, and any bank site will require it.

For anyone's info:

At first I had trouble installing IE6 through ie4linux. I kept getting tons of python coredump errors.

But after trial and error, I realized that I needed to cd to my home directory. I'm not sure why I was getting those errors, but it seems that at first, ie4linux installs from the desktop, but it winds up in the home directory. Here's the code (simple, ain't it?):

```
cd /home/<username>/ie4linux/
sudo ./ie4linux
```

When I did that, the whole process happened, and ie6 now runs great. The install includes Flash and ActiveX, and now I'm ready to view Korean websites from Linux.

---

### Post by methodical on 2008-01-03
Hi I am having trouble running IEs4Linux. I need it for web development, and I use a particular site that doesn't go well with other browsers.

This is what I am getting when trying to run...

```
rswilley@desktop:~/ies4linux-2.99.0$ ./ies4linux
/home/rswilley/ies4linux-2.99.0/ui/pygtk/ies4linux-gtk.py:268: GtkWarning: gtk_text_layout_real_invalidate: assertion `layout->wrap_loop_count == 0' failed
  self.textbuffer.insert_with_tags(self.textbuffer.get_end_iter(), line, tag)
ui/pygtk/python-gtk.sh: line 6: 10097 Segmentation fault      (core dumped) python "$IES4LINUX"/ui/pygtk/ies4linux-gtk.py

```

---

### Post by fireboy129 on 2008-01-03
> **adityakavoor said:**
> opera does what ie can do

yes. opera is my browser of choice. even if you absolutely have to use IE, dont.

it sucks.

---

### Post by jslmg on 2008-01-03
> **methodical said:**
> Hi I am having trouble running IEs4Linux. I need it for web development, and I use a particular site that doesn't go well with other browsers.

This is what I am getting when trying to run...

```
rswilley@desktop:~/ies4linux-2.99.0$ ./ies4linux
/home/rswilley/ies4linux-2.99.0/ui/pygtk/ies4linux-gtk.py:268: GtkWarning: gtk_text_layout_real_invalidate: assertion `layout->wrap_loop_count == 0' failed
  self.textbuffer.insert_with_tags(self.textbuffer.get_end_iter(), line, tag)
ui/pygtk/python-gtk.sh: line 6: 10097 Segmentation fault      (core dumped) python "$IES4LINUX"/ui/pygtk/ies4linux-gtk.py

```

Check the top level of your home folder, not the desktop. Is there an ies4linux folder there? If so, cd into that. Then execute. I had a similar problem with Python when I first tried to run it, but cd'ing into the home folder worked. Of course, if there is no ies4linux folder there, this doesn't apply.

---

### Post by methodical on 2008-01-03
Hmm it works for some reason now. I'm running it from the same dir as earlier.

---

### Post by jslmg on 2008-01-03
> **fireboy129 said:**
> yes. opera is my browser of choice. even if you absolutely have to use IE, dont.

it sucks.

No ActiveX in Opera...

---

### Post by mariodlg on 2008-06-10
> **methodical said:**
> Hmm it works for some reason now. I'm running it from the same dir as earlier.

I had the same problem, and then, it just works, same situation like you.
Those happens because I quit the terminal where I make the ies4linux instalation. 
In a new terminal, the segmentation fault doesn't happens. I don't know why, just it works..

Regards

---

