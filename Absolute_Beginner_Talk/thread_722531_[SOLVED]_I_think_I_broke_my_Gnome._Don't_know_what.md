---
title: "[SOLVED] I think I broke my Gnome. Don't know what to do. Back to old reliable window"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by linuxjerk on 2008-03-12
ok now I think I broke my gnome. I got some kind of gnome error saying some things might not work. Guess what? they don't

Don't have a clue what happened. Tell me where to look for error logs !!!

Whenever I try to minimize things they just disapear. Doesn't matter what they are as soon as I press the minize button they're gone for good.

Anyone know how to fix this? Can I reinstall gnome? Am I screwed and have to reinstall ubuntu?

Now I tried to reboot and I don't even get the top panel buttons. There isn't even a shutdown button.

I'm getting constant hard drive activity. Is there a scan disk like thing in ubuntu??

I'm back to my windows machine because ubuntu is screwed.

Unless someone can tell me how to find out what the error was I guess I'll have to reinstall.

Help!!!

---

### Post by jan quark on 2008-03-12
> ok now I think I broke my gnome. I got some kind of gnome error saying some things might not work.

what exactly did you do? do you have changed something?

what error message do you get? please be more specific

---

### Post by linuxjerk on 2008-03-12
Well as far as I know I didn't do anything today. Booted up normaly this morning.

I have been trying to get a game running in it's own x session. But I kind of gave up on that.

First there was the above mentioned gnome error. Then windows would not minimize.

Now there are no buttons at all on the top panel. So I can't run firefox or open a terminal or shutdown normaly.

When I press the startup button on the computer I get a shutdown panel.

I'm not getting any error messages now, just nothing works.

I'm clueless. Have any iteas of what to do or try?

---

### Post by linuxjerk on 2008-03-12
Can I reinstall Gnome???

Or do I have to start over and reinstall ubuntu??

Ubuntu will never become a serious os unless you can copy your system so you can restore
when things like this happen.

Whoops, I guess you can't do that with XP either can  you!

---

### Post by sports fan Matt on 2008-03-12
When I press the startup button on the computer I get a shutdown panel...thats odd

I had the same happen to me with xubuntu a few days ago..What happens if  you try and get xubuntu?  Can you get to a terminal?

---

### Post by drbob07 on 2008-03-12
You should be able to reinstall GNOME, I would be of more help if I were at home and able to look at the package lists. However try running
```

sudo apt-get --reinstall install ubuntu-desktop

```
In a terminal, then reboot, and see if that solves your issue. Like I said I can't look up packages right now, or I could give you a more specific list, but the above command should be able to fix most things.

---

### Post by Tews on 2008-03-12
I had that happen earlier today .. a simple reboot fixed it for me .. Good Luck :)

---

### Post by linuxjerk on 2008-03-12
How do I run xubuntu matt?

That might  work if I could get a terminal.

Will that work from the rescue terminal?

---

### Post by linuxjerk on 2008-03-12
Tried that from the recovery terminal drbob07 . Says unable to resolve some internet address.

Guess you can get aps from the internet from the recovery terminal.

Sorry a reboot isn't helping here.

What else can I do from the recovery terminal to find out what happened?

Gnome does come up just there aren't any buttons or quick launce to press.

There are some folders on the desktop but don't know of what help that would be.

---

### Post by justsomedude on 2008-03-12
If you have a wireless connection, log in to Gnome first, then use Ctrl + Alt + F1 to get to a terminal session.

Otherwise you won't be connected (if you use Network Manager).

Question: Can you add applets to your panels? Right click them and select "Add to Panel..."

---

### Post by linuxjerk on 2008-03-12
Hey justsomedude

I was able to get to the terminal with crtl-alt-f1 and back with crtl-alt-f7

Yes I can add aps to the panel about all I recognize it the clock. How do I put back the stuff?

I still can minimize windows to the bottom panel though.

---

### Post by Hallvor on 2008-03-12
> **linuxjerk said:**
> 

Ubuntu will never become a serious os unless you can copy your system so you can restore
when things like this happen.


Mandriva and PCLinuxOS has a tool called mklivecd that makes a perfect clone of your partition into a live-cd. It is great if you like to tweak and something goes wrong...

A similar tool is also made for Ubuntu:
[http://www.ubuntu-unleashed.com/2007/09/remaster-and-clone-your-ubuntu-install.html](http://www.ubuntu-unleashed.com/2007/09/remaster-and-clone-your-ubuntu-install.html)

---

### Post by justsomedude on 2008-03-12
Add:

(upper Panel)
Menu Bar
Notification Area
Shut Down
Volume Control

(lower panel)
Show Desktop
Window List
Workspace Switcher
Trash

...and whatever you like. You can move every applet with right click --> move (if it isn`t locked).

If you want a program launcher, right click it in your menu and select "Add this launcher to panel".

---

### Post by linuxjerk on 2008-03-12
I can add stuff to the panels. Don't know how they got removed.

How do I reset it back to the default???

---

### Post by justsomedude on 2008-03-12
Well, add the stuff I mentioned above. 

Are you missing something after that?

---

### Post by linuxjerk on 2008-03-12
Thanks justsomedude  for your help.

I guess my gnome wasn't as broken as I thought. Just alot of things got deleted.

I mostly have thinks back to normal. I didn't realize how flexible ubuntu can be.

I may rearrange things a bit and just leave them there. Boy I was all ready to reinstall

sure glad I took a or two and asked for help.

Thanks Hallvor when I get a minute I'll check out that tool for system backup

---

### Post by handydan918 on 2008-03-12
> Back to old reliable windows

Waht version is that? I've run every version from 3.1 on up and I never found the reliable one....:biggrin:

---

### Post by sports fan Matt on 2008-03-12
Me neither...Sorry i stepped out for a few hours, but All i did was searched for xubuntu in symnpatic and installed...but im glad gnome is working well...

---

### Post by Hallvor on 2008-03-13
> **linuxjerk said:**
> 
Thanks Hallvor when I get a minute I'll check out that tool for system backup

It is a great tool. It saved me of a full reinstall a couple of weeks ago when something broke. I had the system back up in less than 30 minutes.

---

