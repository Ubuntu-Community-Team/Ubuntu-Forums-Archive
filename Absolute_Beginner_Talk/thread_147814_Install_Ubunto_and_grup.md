---
title: "Install Ubunto and grup"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-03-20
Hi Im new to Ubunto and using Grup.

I just installed Ubunto and it detected my WinXP and ask me to install Grup as well. I hit yeah, and it told me to reboot and remove the CD. After loading for a while, it opens Grup. 

Now I dont know what to do? I tryid mustly all of the commands in Grup, but I cant figure how to boot into either Windows or Ubunto to complete the installation.

Can anyone help me with this?

---

### Post by m.musashi on 2006-03-20
[This page](http://users.bigpond.net.au/hermanzone/p15.htm) shows some screen shots of the grub boot loader. Is that what you are referring to? Do you have similar options to those listed? If so, what is happening to prevent you from booting either one?

EDIT If you get the grub menu with the ubuntu option you should just be able to press enter and boot ubuntu. XP should also be near the bottom. If you arrow down to it and press enter you should be able to boot XP. Can you explain what happens if you try this?

---

### Post by aktiwers on 2006-03-20
Yes I get number 2 screen!

with the grup> 

What shall I do here? I want to complete the installation of Ubuntu and be able choose between Ubuntu and Windows in the future.

---

### Post by aktiwers on 2006-03-21
Thanks! I followed the guide and it all worked out.

Writing from Ubuntu now :) 

Thanks

---

### Post by m.musashi on 2006-03-21
You shouldn't get that screen. You should get the first one. The one that looks kind of like ```
ubuntu, kernel 2.6.x.x
ubuntu, kernel 2.6.x.x (recovery mode)
ubuntu, kernel memtest86+
Other operating system
Microsoft Windows XP
```

If you are booting into grub and getting the second screen on that link page then something isn't right. Unfortunately, I don't know what that could be. Looking over the grub page I linked you to I see that you can get back to the GUI menu from the command line interface that you seem to be getting by pressing esc. What does it do if you do that? It also says you can reboot by typing 'reboot' and pressing enter. What does that do?

The page also talks about booting ubuntu from the command line and gives some instructions for doing that. Try going through those if you can't get the GUI menu to load. If you can get ubuntu to boot it will finish the install and from there you might be able to track down the problems with grub.

I'm really not a grub expert and I've never seen what you seem to be seeing. Try a few things from that grub how to page and see if you can get it to work. If not, post back and I or hopefully someone with more knowledge can try and figure it out.

EDIT: oops, guess I was too slow. You seem to have worked it out. Great because I wasn't sure where to go next. Welcome aboard.

---

### Post by aktiwers on 2006-03-28
Well Actually I didnt get it to work 100%.

It still opens up in the 
Grub>  
thing. But when I type in " root (hd0,2) " and hit enter, I can press Esc, and get to the first menu. From there I can boot up in Ubuntu. 

I do also have XP installed (but I am seriosly thinking of deleteting it though, after using this wonderful Linux for a week), and it somehow got currupt. It wont boot. Maybe thats the reason grub starts up this way?

Well, its getting pretty annoying, so if anyone knows how to make it boot up on screen 1, I would be more than happy to know :)

And thanks for the help so fare!

---

### Post by m.musashi on 2006-03-28
Something doesn't sound right but darned if I know what it is. You should get the text menu similar to the example I posted above. It's nothing fancy but works. If you have to go through some voodoo dance to get it to boot then there is problem looking to be solved.

I think it's great if you are ready to dump windows however, I would hold onto it for now (assuming you can get it to boot). I dual boot because there are just times when I need windows (macromedia stuff) or just in case. It's kind of nice having a choice. However, as soon as I can find a way to do everything in Linux windows is toast.

As for your problem, if you are willing to dump windows then a clean install of ubuntu might be a good choice. If you have your windows CD then you can always go back. Just make sure you save anything you don't want to lose. Everytime I do a clean install I end up forgetting something (web favorites, etc).

---

### Post by aktiwers on 2006-03-28
Hehe yeah the favorites thing I have done a few times my self.. Or even worse, I once saved my Firefox (empty) favorites list and overwrited my backup list, instead of loading it! ](*,)   5 years of Favorites gone! ](*,) 

Well back to topic.
I will try to fix the XP (some files where currupt), and then I will report back how it went. If it fixes my problem it would be great, but if anyone else has any suggestions, your more than welcome. Thanks.

Will report back tomorrow (its late here 5:29 AM), so Im off to bed. Thanks for the fast support! :)

---

### Post by sn123 on 2006-03-28
[QUOTE=aktiwers]Well Actually I didnt get it to work 100%.

It still opens up in the 
Grub>  
thing. But when I type in " root (hd0,2) " and hit enter, I can press Esc, and get to the first menu. From there I can boot up in Ubuntu. 
[/QUOTE]
AFAIR, Grub falls back to the command line interface if it doesn't find the menu.lst file under /boot/grub or if **hiddenmenu** command is used in menu.lst file. Could you just check whether there is indeed menu.lst file under /boot/grub and "hiddenmenu" is not in the file.
```

$ cat /boot/grub/menu.lst

```
You can also try grep:
$ grep hiddenmenu /boot/grub/menu.lst

S

---

### Post by m.musashi on 2006-03-28
5:30 AM!!? Sounds like time to get up :). You must be somewhere near the PM. How's the weather over there?

I had another thought. There is a way to just reinstall grub without doing a whole new ubuntu install. I would be nice if that was on the CD. I think I saw it on the Fedora core 5 install as an option. I'm not sure how to do it, though. I'll search around a bit and see if I can find it.

EDIT: or what sn123 just said. Sounds like a possibility. However, I think the hidemenu option just hides the boot options unless you press escape with 3 seconds (I think that's the default behavior). Pressing escape brings up the regular boot menu.

EDIT2: okay, did a little searching and found [this thread](http://www.ubuntuforums.org/showthread.php?t=24113). Sounds like a couple options for reinstalling grub. I don't know if that will fix the problem but whenever I've called a tech support number they always tell me to reinstall so it must be the right option :mrgreen:.

---

