---
title: "Can I use a GUI in Ubuntu Server"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by gavbell on 2007-02-02
sorry if this is a bit dumb. Being a long time Windoze user and trying to get into Linux for some time, I decided to try using Ubuntu and to set it up as a simple server for file sharing and perhaps a simple email server. I am using VMWare Server and have downloaded the pre-built Ubuntu 6.10 Server package. The trouble is, when I try to use SUDO APT-GET UPDATE there appears to be a problem connecting to the Internet and being new to Ubuntu, I thought it might be easier if I could start a GUI and I think I could manage to work out how to set the Networking up to use DHCP - the command line thing is a bit strange to me at the moment. Can anyone suggest how to do this?

Thanks.

P.S. I did try to search for this but couldn't find anything helpful.

---

### Post by Bachstelze on 2007-02-02
Download an Ubuntu/Kubuntu/Xubuntu (depending on whether you want GNOME, KDE or XFCE) alternate CD. Then in your server, run 

```
sudo apt-cdrom add
```

insert your CD and when APT is done scanning it, run

```
sudo aptitude install ubuntu-desktop
```

to install your GUI. Replace ubuntu with kubuntu or xubuntu if needed.

---

### Post by gavbell on 2007-02-02
how do I now start the desktop?

I tried STARTX, but that does not work (both with and without SUDO).

Thanks.

---

### Post by steve.horsley on 2007-02-02
"does not work" is a bit vague. What happened? What did it say? 

It should be **startx**, not **STARTX** by the way. Linux is case sensitive.

---

### Post by Bachstelze on 2007-02-02
you could also do

```
sudo /etc/init.d/?dm start
```

---

### Post by shallow on 2007-02-02
disappointed
wow am i disappointed i know i will beat up for this

i had the same question about the GUI. i loved the ubuntu desktop software, i was honestly thinking of different ways i could add this into our company
i downloaded the server edition installed it and go to a text propt

i started thinking i did something wrong the desktop version is in GUI they must have been smart enuff to make there server GUI.
i did the steps you showed us here. thank you for that. 
but it didnt work. 
i could spend the next few hours trying to figure out how to get the server to run on gui but to be honest its not worth it. i really hope that linux people build some type of server software that is graphic its easier to run to understand and to use. 
i was so excited by the desktop i thought i could finally move our IT away from evil microsoft. 
this is a great communtiy but still light years away from ever becoming really being used

---

### Post by Perfect Storm on 2007-02-02
I think you misunderstood the concept. Most servers don't need GUI in fact servers are better without a GUI (More stable, less resources, better performance, less security holes).
If you are sesrious of thinking using a server I recoomend that you read up on how to use command lines as a start. Yes this might be a bit intemidating for a windows user, but the reward in the end is prizeless.

---

### Post by steve.horsley on 2007-02-02
> **HymnToLife said:**
> you could also do

```
sudo /etc/init.d/?dm start
```

That questionmark should be a g:
sudo /etc/init.d/gdm start

---

### Post by bodhi.zazen on 2007-02-02
I agree 150 % with Artificial Intelligence !

I would add, what did you expect ? Linux is a whole new OS and it is unlikely you will be able to convert overnight.

With that said:

First, go ahead and install Ubuntu desktop. It will give you a full featured OS and can be used as a server. Once you are comfortable with Linux you may want to do away with the GUI.

Second, check out [webmin](http://www.webmin.com/)

Third, here is an intro to the CLI: [http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

HTH :)

---

### Post by shallow on 2007-02-02
"AI" I really do understand the concept
Most servers and most desktops don’t need GUI. 
With out that graphic, it doesn’t allow you the admin to see multiple things, its tuff to fix things because most of the times you need to look at a problem in multiple areas. I will have one window open with the problem another diag of the problem another with the fix to the problem and you can’t do that in text based stuff. Most people are visual. You can also to more point and find answer instead of reading code. To be honest I could never be a programmer just because I get sick of seeing the words. All the myself stuff I have to do sucks ha-ha. But it’s a great program. Its not a bit intimidation is very intimidating. If I can do the same thing in a guy vs. txt I will always go with the guy program. The reason why Linux isn’t number one in the world isn’t because it’s not better than F-in evil Microsoft it’s because it’s too much code. I read up and believe me I know Linux is way ahead and better then MS. but until they get a better user face it won’t happen. And ubuntu desktop is going in the right direction, I was so excited using it, that is why I was so sad to see server they way it is.

---

### Post by Perfect Storm on 2007-02-03
Not to burst your bubble but most servers are *nix related and not windows related and there's multiply reasons for that ;)

Yes you find it very intemidating but again you are starting to learn a new system and with all new things it's hard because you don't know how to do this or that. I suggest/recommend that you take bodhi.zazen comments to you and when you feel you are ready to use server without a GUI take the jump.


regards
A.I. Dude

---

### Post by steve.horsley on 2007-02-03
It is tru that servers in general don't need a GUI. That's because you administer them remotely. Most server admin consists of moving and editing files, and the odd command-line bit. 

I use nautilus to ssh remote servers. I drag and drop files, right-click or double-click them to edit them from my desk. The server doesn't have to have a GUI installed. Command line stuff I do with a terminal and ssh. The server doesn't need a GUI installed because it doesn't have a screen connected. The GUI is on my desk.

And it's only intimidating because you've never done it before, like driving a car for the first time. You wouldn't stick with taxis because driving your ouwn car is "too hard", would you? Well, I'd love to be able to afford to say that actually.

---

