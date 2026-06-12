---
title: "help with netgear pci adapter WG311 v3"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by MolotovHearts on 2007-10-08
Hello. I know this has been talked about multiple times before, and sorry to bring it up again but I'm having trouble getting onto the net with Netgear WG311 v3 wireless pci adapter.

I tried the instructions on the ubuntu help wiki and some other instructions i found on this forum but have still had no luck.

I just got ubuntu so i guess i have the newest version. any help would be great. sorry again for this recurring topic.

- luke.

ps. at the moment i have to come on here (windows xp) then back onto ubuntu to try all the stuff i been reading. is there an easier way?

---

### Post by MolotovHearts on 2007-10-08
is anyone able to help?

---

### Post by MolotovHearts on 2007-10-09
i've got the ndiswrapper and i've installed the driver that is meant to be the one i need.

when i type ndiswrapper -i WG311v3.INF it tells me its installed

when i type ndiswrapper -l it then tells me that the driver is invalid.

and that's as far as i can get, and am unsure what to do after that. i've also tried a few different drivers (that might just be the same) and they all come up as being invalid.

would anyone be able to help with this?

---

### Post by redmonster13 on 2007-10-10
I went through this about 2 months ago and with the amount of work I had to do to get it to work I honestly wouldnt recomend it. If you are intent on using that particular adaptor I will see if I can hunt down the 4 or 5 different tutorials I worked with to get it functioning.

---

### Post by MolotovHearts on 2007-10-10
that would be really cool if you wouldn't mind doing that. i don't really want to have to buy new hardware if there is the possibility of succeeding in making it work.

because i've tried a few times and ended up not making it all the way through, getting stuck on some points along the way, do i have to uninstall what i've already done and then start again? if so, how do i do that? i'm not entirely sure.

i think the main thing at the moment is that it always comes up saying the drivers are invalid.

---

### Post by kishe on 2007-10-10
1) Are you using 64bit Ubuntu? If you are, are the driver you are trying to set up through ndiswrapper 64bit?

2) Have you done ndiswrapper -m?

---

### Post by MolotovHearts on 2007-10-10
>  1) Are you using 64bit Ubuntu? If you are, are the driver you are trying to set up through ndiswrapper 64bit? 

I'm unsure of what I'm using. I used wubi to download ubuntu, but I'm unsure what one got downloaded. How do i find out if I'm using 64bit or 32bit?


>  2) Have you done ndiswrapper -m? 

Not yet. But i will try it.


Thanks.

---

### Post by redmonster13 on 2007-10-10
ok, I am going to look around and see if I can find what worked for me.

First get wicd, it is the program that finally let me manage my wireless.

I will post back here again when I find the rest of what I did.

---

### Post by redmonster13 on 2007-10-10
I think this was the tutorial that finally worked, although I did have to go through 3 or 4 before this so it could have been a combination of things.

[http://www.jimbo7.com/wiki/index.php?title=WG311v3](http://www.jimbo7.com/wiki/index.php?title=WG311v3)

---

### Post by MolotovHearts on 2007-10-10
If it possibly helps in helping me:

# ndiswrapper -i WG311v3.INF 
installing wg311v3 ... 
couldn't open WG311v3.INF: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174. 

# ndiswrapper -l 
wg311v3 : invalid driver! 

# ndiswrapper -m 
module configuration already contains alias directive 

# ndiswrapper -a 11ab:1faa WG311v3 
ls: /etc/ndiswrapper/WG311v3/: No such file or directory 
driver 'WG311v3' is not installed (properly)! 

These are what i get if I enter those four things into the terminal. I went to usr/sbin and found out I have two ndiswrapper files, one is just “ndiswrapper” the other is “ndiswrapper-1.9”. Is it ok to have both of these or does one have to be removed?

I keep finding out things everytime I try different things so this is kinda fun, but I still don't know if I'm getting any closer to internet access.

Thanks for the link and the advice. I already tried the instructions in the wiki and i wasn't able to get them to work, but that could possibly due to combining it with other instructions and drivers or maybe not. Its possible that I might have misunderstood a few of the instructions so i should probably try them again a lot closer and also because I'm new to linux so still trying to work out some of the basic terms, functions, etc.

---

### Post by redmonster13 on 2007-10-10
When I was going througn it I found that I had to follow the instructions pretty closely, however there were a few parts that I had to run under sudo.

The problem is I dont remember which parts.

---

### Post by HackCoders on 2007-10-11
I have the same card, and having same issue as you :(

---

### Post by MolotovHearts on 2007-10-11
It's horrible ay?! It's restricting my ability to liberate myself from windows even more.

I haven't had the chance to try anything else, but tonight i might try downloading wicd and seeing if that helps.

---

### Post by anewguy on 2007-10-12
It looks to me that in your case you didn't specify the path to the .inf file and it didn't find it.  What you need to do is:


-  sudo ndiswrapper -r WG311v3.INF       this will remove the erroneous pointer to a non-existant file

- sudo ndiswrapper -i  {full path to}/WG311v3.INF   - if you are sure the file was in your default path, then maybe you misspelled it (remember - Linux is case sensitive)

- continue on with your other stuff

If any of these steps gives an error, stop, copy the error, and post back here.:)

---

### Post by MolotovHearts on 2007-10-12
thanks, i'll try that soon.

by the way, what is meant by the "default path". sorry, i'm still learning all the terms and such.

---

### Post by MolotovHearts on 2007-10-12
My wireless card was finally recognised by my ubuntu. But I still couldn't connect to the net. 

In the network manager it finally showed wireless as a choice but still wasn't working.

When I clicked on the little networking logo on the top taskbar it listed three wireless networks i could choose from. The one that i use for XP was there so I clicked on it and I had to enter a code to be able to connect to it. I didn't have it so I went back into windows and changed the WPA (i think it was that) and saved a copy of it in openoffice then in ubuntu opened it and put the code in there to go on the net. It didn't seem to work though. It said it had a 23% connection but I was still unable to get to anything except the home page.

I don't really know what to try/do.

Also, how do I get it so it's automatically there everytime I restart ubuntu. It wasn't there last time. I tried the instructions for it but I don't think it worked.

I know this is really vague, so if any more info is needed I will go get it, I just wasn't able to copy/past anything from terminal because it went kinda weird and my computer froze so i restarted.

---

### Post by Count Doofus on 2007-10-21
You'll get that error @ line 174 if the case of the filename  is wrong !
Might want to check it out. I got me goo for three DaYs.InF

had the same problem with my Marvell card. Looked for every kind of solution that concerned hardware interface on the PCI bus.

The Real Problem was every time I issued the 
blablabla:~$ sudo ndiswrapper -i mrv8000c.inf 
I got - No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174

Until I typed the filename with the correct CASE - Mrv8000c.INF - 

GRRRRRRRRR!%@$#$###!$!@@!$@!@#!

---

### Post by MolotovHearts on 2007-10-22
i've kind of given up on ubuntu at the moment. for some reason my ubuntu wasn't even booting so i removed it by uninstalling wubi. I realised I don't really have the time for it at the moment, but look forward to getting it going again after I finish school in about a month. The only problem I have now is that my internet on Windows isn't even connecting. So I have no idea what's happened.

---

### Post by TheIrishGuy on 2007-11-13
[http://ubuntuforums.org/showthread.php?t=592137&highlight=wg311v3](http://ubuntuforums.org/showthread.php?t=592137&highlight=wg311v3)

---

