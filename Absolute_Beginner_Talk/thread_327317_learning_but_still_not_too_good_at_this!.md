---
title: "learning but still not too good at this!"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by hairmetal4ever on 2006-12-29
OK - I am learning how to use both the command line and the Synaptic package manager.  However, I'm still confused.

I installed WINE last night to try it out, and can't actually find the program to run it.  It's not in my menu anywhere I see, but there is a "Wine" folder in my usr/lib/ directory.

I STILL can't get anything to play in .wmv, .avi, or .mpg.  I can play embedded videos like on youtube but nothing of the above.  I read somewhere I need to download some win32 drivers from Mplayer into my win32 folder, I did download something there, but when I open the file in  Archive Manager, I try to extract, it says I need a password, yet the password box is grayed out.  HELP!!  ](*,) ](*,)

---

### Post by EZEN on 2006-12-29
[**https://help.ubuntu.com/community/RestrictedFormats**]("https://help.ubuntu.com/community/RestrictedFormats")
Here is a link that one of the experts passed me last week.
Pay particular attention to "**How To Get Things Working In A Hurry**".
Log into a console and copy and paste that code.
Worked fine for me.
For most of the formats anyways...
All the others are mentioned there as well.
B)

---

### Post by MasterOfDisaster on 2006-12-29
Wine is run from the commandline, and is typically run 'wine pathtowindowsexe'.  For more complete info go to:

[http://www.winehq.com/site/docs/wineusr-guide/index](http://www.winehq.com/site/docs/wineusr-guide/index)

There's a lot there, but its pretty complete.

In regards to your codecs problem, I would recommend Automatix:

[http://www.getautomatix.com/](http://www.getautomatix.com/)

Its a nice and easy program to use that can install pretty much every common codec or program for Ubuntu.

Anyways, cheers.

---

### Post by hairmetal4ever on 2006-12-29
What is the "Add/Remove" for under the "Applications" tab?

---

### Post by Jorge32 on 2006-12-29
Add/ remove is for adding or removing applications, bu for me is more comfortable using the synaptyc package, because it tells you if an application needs anything else than just the application, and you could easily install it from there.
By the way, with wine, why don't you try with this? 
```
sudo winefile
```
it should open a window from where you could run installations, and then you enter normally from the applications menu, or desktop, or launcher (it depends how you installed it)

---

### Post by hairmetal4ever on 2006-12-29
It worked, but it doesn't DO anything.  It just has a Z and C drive. The Z drive appears to be all my Linux folders and C is nothing but empty folders.

---

### Post by Jorge32 on 2006-12-29
try running an .exe app, install something. Then you should be able to enter it from a launcher ( in desktop or panel if you created those) or in the applications menu, almost at the end a  folder named wine will appear, with the programs. or for example, for me in XFCE thast folder appears as "others" in the app menu.

---

### Post by Apple 101 on 2006-12-29
You need to run 'winecfg' first.

---

### Post by hairmetal4ever on 2006-12-29
> **Apple 101 said:**
> You need to run 'winecfg' first.

sudo winecfg?

---

### Post by d3v1ant_0n3 on 2006-12-29
Just ```
 winecgf
``` should do it.

Not all Wine installed programs seem to end up in the 'Wine' menu entry for me, not sure why exactly.

You can find your wine folder (and it's installed programs) in your /home folder -its a hidden folder named .wine .Inside that folder I have a folder named 'Drive_C' which then has a 'Program Files' directory a la Windows.

---

### Post by raul_ on 2006-12-29
yes that should do it..but why not searching for a tutorial here in the forums? is says everything you need to know
:-k it's faster than posting and waiting for the replies

---

### Post by Jorge32 on 2006-12-29
Look, maybe this is an usefull link for you:
[http://www.winehq.com/docs/en/wineusr-guide.html#WINE-FEATURES](http://www.winehq.com/docs/en/wineusr-guide.html#WINE-FEATURES)

---

### Post by hairmetal4ever on 2006-12-29
So if I want to install a windows program, that's where I save the file?

---

### Post by AndyCooll on 2006-12-29
> **hairmetal4ever said:**
> I STILL can't get anything to play in .wmv, .avi, or .mpg.  I can play embedded videos like on youtube but nothing of the above.  I read somewhere I need to download some win32 drivers from Mplayer into my win32 folder, I did download something there, but when I open the file in  Archive Manager, I try to extract, it says I need a password, yet the password box is grayed out.  HELP!!  ](*,) ](*,)

Follow the link in my signature about Restricted Formats. That'll sort you out.

:cool:

---

