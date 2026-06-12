---
title: "Help me install vid drivers by command lines"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by -Ghost9- on 2007-02-05
ok. i finally got my stuff so that it will boot up with grub. only took losing everything twice. but whatever.

Now i'm back to the problem where the screen locks up at loading cause I used the 6.10 to install, since that's all i've been able to get working install wise and it won't detect my video or something.

Can someone help me install ati vid drivers for an x850xt through the recovery mode?

---

### Post by bodhi.zazen on 2007-02-06
I am no expert with ATI

See if this helps:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

From CLI:
```
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.7.5-0ubuntu1_all.deb
sudo dpkg -i envy_0.7.5-0ubuntu1_all.deb
```

Or this:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by -Ghost9- on 2007-02-06
> **bodhi.zazen said:**
> I am no expert with ATI

See if this helps:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

From CLI:
```
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.7.5-0ubuntu1_all.deb
sudo dpkg -i envy_0.7.5-0ubuntu1_all.deb
```

Or this:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

no go. no matter what I try I get a failure to resolve message. it's like i'm not getting a net connection through linux. I guess I'll try installing 6.06 in place of 6.10 and see what i can do with that.

---

### Post by bodhi.zazen on 2007-02-06
It looks like the server is down ... :(

Try later ...

---

### Post by -Ghost9- on 2007-02-06
i tried inside of the live cd. I ended up getting rid of edgy and installed dapper. I think i might be getting the hang of this. I reorganized the partitions since I took too much away from windows so now that's all set up.

Now I dunno if the live cd stuff worked or what, but now My screen res has gone higher. I'm at 1280x1024, and i'm not sure why :) I need to figure out if my vid card is actually being utilized cause i'm not sure it is. video still seems kinda slow, but atleast i have something up and running!!!!!! 

Things do look a bit different in linux. I'll have to play more later. so tired. Thanks for all the help.

---

### Post by -Ghost9- on 2007-02-06
i'm pretty sure my card isn't being utilized. I downloaded the amd driver installed for my ati card, but don't know how to run it. 

I've been trying to follow the instructions here:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.33.6-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.33.6-inst.html)

but i either don't know how to navigate to the file or something cause I end up getting this error all the time:
No such file or directory

I even adjusted the file name cause i thought it was wrong compared to the file they have for download, but no luck. in the terminal it says "desktop" and that's where i downloaded it too. is there a dual meaning to the work desktop in the terminal?

---

### Post by -Ghost9- on 2007-02-06
nevermind. got it. sorta. i think i got it installed. now i need to figure out how to configure. the directions seem outdated.

---

### Post by bodhi.zazen on 2007-02-06
See if this helps:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

(sorry I wish I know more about ATI)

---

### Post by -Ghost9- on 2007-02-06
followed the instructions and it seems to have worked! Not sure how to test it yet, but i got positive results according to the instructions. I supposed if I give beryl a shot I'll know for sure.

---

