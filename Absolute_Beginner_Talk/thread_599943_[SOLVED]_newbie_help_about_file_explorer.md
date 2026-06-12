---
title: "[SOLVED] newbie help about file explorer"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by kristiaan_d on 2007-11-01
Hi all,
just done my first installation of ubuntu 6.06 LTS (got it free with an Ubuntu unleased book)

i am having some problems editing files in the file explorer, things like xorg.conf i know its a protected file in the OS so it wont let me rename it or change it etc. my biggest problem is HOW DO I DO IT without going to the command line....

i have to admit i have a mac and it grates on my nerves that i cannot do it on there either without having to resort to the command line this is something that has always anoyed me on all unix based systems....

please help me out. i am trying to run ubuntu on parrallels on os x but its default screen res is higher than my macs so it goes offscreen and i cannot get it to change to a smaller res.

---

### Post by Arthur Archnix on 2007-11-01
Hackers and virus writers also find this kind of stuff in Linux annoying, so you're not alone! As for your question, there are a couple ways I can think of...

1. Every time you want access to a protected file in nautilys, open nautilus using the command:
```
gksudo nautilus
```

If you don't want to type that into a terminal you can create a shortcut in your menu. Use the menu editor to create a new entry, call it Super Nautilus or something and enter the command above, choose an icon, bam, bob's your less secure uncle.

2. You can add an option in nautilus, to right-click and open restricted files. Instructions are [here]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_browse_files.2Ffolders_as_root_user_in_Nautilus").

Considering what you're asking for, I'd go with option 2.

---

### Post by nick_h on 2007-11-01
You need to install the package *nautilus-gksu*.  This will give you an "open as administrator" option in nautilus.

Run System->Administration->Synaptic Package Manager to install it.

---

### Post by kristiaan_d on 2007-11-01
Hi Arthur,
thanks for the quick reply, i agree with you in respect to what its there for i think its brilliant, thats why when i needed a new system i bought a mac over a vista system... there prettier, faster, more intuitive to use etc.

but as i mentioned this has always been one of the simple things i would have expected to be catered for in linux distros but none of the ones i have ever used in my past do it...

thanks again for the solution i am now going to go tinker with my resolution.

---

### Post by kristiaan_d on 2007-11-01
ok i have to admit i have now broken my new installation and have no idea how to fix it.....

i am trying to get the video resolution down to 800X600 for my macbook 13" widescreen, i followed some instructions i googled which were funnily enough on here and now when i login to the system it makes a drum beat sound and logs me off.....


any suggestions on this one???

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by Arthur Archnix on 2007-11-01
No problems, by the way, the link I gave you gives step by step instructions that achieve the same thing that Nich_H suggested. I wasn't aware that it was available in Dapper, but if it is you may find that quicker and easier.

---

### Post by Arthur Archnix on 2007-11-01
If you have a newer macbook you would be better off installing either Feisty or Gutsy. I'd try Gutsy first since there are significant improvements in the Kernel for laptops and battery usage. Most of your book would still be relevant. 

In any case, you should start  a new thread for unrelated questions (more likely to be read and answered quickly), and don't forget to mark your solved threads solved using thread tools.

If you followed the advice on that link all you have to do is boot to the command line and replace your xorg.conf with the backup you made. But again, that should go in another thread.

---

### Post by kristiaan_d on 2007-11-01
again thanks arthur will mark this as answered now, i was thinking about doing the newer version but from what i have read about the load unload problems i think i will wait (apple hardware is not cheap lol)

plus i could not get the new version of ubuntu to install in parallels on my macbook the live cd starts up then just black screens on me...

another problem for another thread lol 

thanks again
kris

---

