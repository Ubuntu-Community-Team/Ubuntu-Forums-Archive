---
title: "Black now shows green (MacBook Pro)"
date: 2016-08-30
forum: Apple Hardware Users
---

### Post by jsnklln on 2016-08-30
I've got a macbook pro running kubuntu (Ubuntu 16.04.01 LTS) some time in the last week or so the blacks started showing up as green bars (check the bottom of the attached picture).  I kinda expected this to be hardware related and went through some suggestions I found on the web.  None of them helped.  The kicker is if I boot to the mac os it doesn't happen.  It does show up in the boot loader.  Any suggestions?

[IMG]https://s17.postimg.org/dplfmilfz/greenisthenewblack.png[/IMG]

---

### Post by howefield on 2016-08-30
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by &amp;KyT$0P# on 2016-08-30
Er, I don't see any such effect in the attached picture.  Can you please re-take the attached picture as a photo of the screen?

---

### Post by jsnklln on 2016-09-01
So here's a picture I took of the picture I posted in the original.  All the green bits should be black.

[IMG]https://s14.postimg.org/51g0mpxip/photo_4.jpg[/IMG]

---

### Post by &amp;KyT$0P# on 2016-09-01
Gak.  Does that particular black color (looks like #232629 according the screenshot in the first post) render normally anywhere?

What kind of MacBook Pro are you using?

Please post the output from running [FONT=Courier New]glxinfo[/FONT] in a Terminal

---

### Post by jsnklln on 2016-09-01
Here's another picture just for kicks, the bad colors are bad every where: 
[IMG]https://s16.postimg.org/4u27njgx1/photo_5.jpg[/IMG]

output of glxinfo is pretty long and the cutting and pasting was going badly so I uploaded it to this somewhat shady looking website in order to have a link to post here.
[http://www.filetolink.com/d170f74e78](http://www.filetolink.com/d170f74e78)

I don't know a lot about it, it's the first mac I ever had.  It was given to me to do work on a few years ago.  It was new then.  It's a MacBook Pro and I'm pretty sure it's the 17 inch.

---

### Post by &amp;KyT$0P# on 2016-09-01
> **jsnklln said:**
> output of glxinfo is pretty long and the cutting and pasting was going badly so I uploaded it to this somewhat shady looking website in order to have a link to post here.
I don't feel comfortable to visit "shady looking website".  Can you use [pastebin]("https://paste.ubuntu.com/")?

> I don't know a lot about it, it's the first mac I ever had.
Probably the easiest way to get the specific information is to install inxi
```
sudo apt-get install inxi
```
and then run this command
```
inxi -Fxx
```
See how it says "MacBookPro9,1" in my signature?  That's the model number of the computer and the equivalent of the info we need to get for your system.  Look for a similar string in your inxi output, in my case it's mentioned near the top of the output with the comma replaced by a whitespace.

---

### Post by jsnklln on 2016-09-02
According to inxi I'm on a MacBookPro8 2
pastebin for glxinfo output: [https://paste.ubuntu.com/23124320/](https://paste.ubuntu.com/23124320/)

---

### Post by &amp;KyT$0P# on 2016-09-02
Thanks.  This is a graphics driver problem.  Looks like you're running on your discrete GPU, which is AMD brand... and AMD drivers are a bit tricky in 16.04, and I'm not the right person to help more with that, others here will know better.

It looks like your Mac has an integrated GPU (Intel graphics) as well.  I run on the integrated GPU and the instructions I used were originally written for 2011 Mac, so I can help you set that up if you'd like to try it.  But I don't use Kubuntu... with KDE 5 being so hardware-acceleration-heavy you *might* get bad performance with the integrated GPU when doing graphics-heavier stuff, I don't know.

---

### Post by jsnklln on 2016-09-02
I kinda had a feeling it was something along those lines but wasn't sure how to deal with it.  Thank you.
I'm not against running on the GPU, I don't do much graphics heavy stuff.  If you're willing to send along the instructions I can step through them and try to sort out the differences for Kubuntu.  In the mean time I'll google around a bit.

Thanks again for all the help.

---

### Post by &amp;KyT$0P# on 2016-09-02
Be careful what you do with instructions you "just find" as most of them for 2011/2012 MacBook Pros were written with Ubuntu 11.* or 12.04 in mind, where many extra complicated steps were required.  We're running 14.04 and 16.04 both of which properly supports our hardware without such complex fiddling.

Also, this information was sourced from links that can be found at the end of this post.  Read through those after reading these instructions, to make sure you understand everything you'll be doing.  This is really important.
**Make a backup before starting this.**  Some of it can get pretty quirky and there is risk of corruption if it's done wrong.

First thing you need is gfxCardStatus version 2.2.1, no other version works.  Download link -
```
https://gfx.io/downloads/gfxCardStatus-2.2.1.zip
```
Install that on your OS X, run it and set the GPU to "integrated only".  Reboot into Kubuntu.

Run glxinfo to check that it worked.  It should say something about Intel, if it doesn't then do not proceed.

Now that you're running on Intel graphics, next step is making sure the discrete GPU is powered off, so that your computer doesn't overheat.  Open [FONT=Courier New]/etc/grub.d/10_linux[/FONT] in a text editor, find this line
```
  echo "	insmod gzio" | sed "s/^/$submenu_indentation/"
```
and stick this right after it
```
  # we're using intel graphics; disable discrete gpu
  echo "	outb 0x728 1" | sed "s/^/$submenu_indentation/"
  echo "	outb 0x710 2" | sed "s/^/$submenu_indentation/"
  echo "	outb 0x740 2" | sed "s/^/$submenu_indentation/"
  echo "	outb 0x750 0" | sed "s/^/$submenu_indentation/"

```
Save and exit.  Now in [FONT=Courier New]/etc/default/grub[/FONT] change the GRUB_CMDLINE_LINUX_DEFAULT - remove quiet and splash, and add the i915 parameter as shown below.  I don't have anything else there, so mine looks like this, if you have any boot parameters other than quiet and splash listed, you probably want to leave them.
```
GRUB_CMDLINE_LINUX_DEFAULT="i915.i915_enable_rc6=3"
```
Save the changes there.  Now run [FONT=Courier New]sudo update-grub[/FONT] to write the changes to GRUB.
(Note that on your next reboot, you will see a lot of log message like text flying by on your screen during boot - this is normal and good)

Almost there, one more step is required.  See the links below for how to fix the problem of the GPU powering on after suspend.  **Do not suspend the computer until all of that is done AND you have rebooted, or the OS may crash and become corrupted.**

Now that all of that is done, reboot and check that it's still OK by runing glxinfo again.


Most of this information was taken from these links.  Again, please refer to them before following any of these instructions, to make sure you understand everything before you start.  Don't do anything you don't understand and do not skip any of the steps I've mentioned.
[https://wiki.debian.org/InstallingDebianOn/Apple/MacBookPro/9-1]("https://wiki.debian.org/InstallingDebianOn/Apple/MacBookPro/9-1")
[http://blog.tkassembled.com/364/intel-graphics-on-a-2011-macbook-pro-in-linux/]("http://blog.tkassembled.com/364/intel-graphics-on-a-2011-macbook-pro-in-linux/")

---

