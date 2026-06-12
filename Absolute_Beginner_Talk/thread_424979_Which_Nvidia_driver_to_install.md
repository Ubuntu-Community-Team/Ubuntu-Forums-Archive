---
title: "Which Nvidia driver to install?"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by destructo on 2007-04-27
Hi there and thanks if you can help me

I have only just installed feisty fawn yesterday and I have not installed any drivers for my new graphics card. I wanted to test some of the games out but they look really choppy and it takes along time to move around in them. So what do i do to get them working? Do i just download one of these files and install it?

I have found this link but i do not know which driver to get

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

do i get this one

**Linux IA64**

or this one? 
[B]
Linux AMD64/EM64T[/B]


Heres the card i have

Nvidia Geforce 8600gt 256mb/128bit/gddr3

any ideas?


Thanks.

---

### Post by Outrunner on 2007-04-27
You just need to do

```
sudo apt-get install nvidia-glx
```

then do
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

and in the drivers list choose nvidia. Choose you're resolution with the space bar

---

### Post by destructo on 2007-04-27
Is that all I need to do?

Did it install all the drivers?, i chose 1600x1200 and then I exited terminal. 

Thanks.

---

### Post by kvonb on 2007-04-27
You could just click on "Restricted drivers manager" from the System->Administration menu, then select "enable".

It will download and install it in one easy operation.

---

### Post by Outrunner on 2007-04-27
> **destructo said:**
> Is that all I need to do?

Did it install all the drivers?, i chose 1600x1200 and then I exited terminal. 

Thanks.

Yes it should work properly now. You'll need to restart the x server after this (CTRL+ALT+BACKSPACE)

---

### Post by destructo on 2007-04-27
okay i restarted and now when i got to do what** kvonb** said, it came up and said 

"your hardware does not need any restricted drivers"

What does that mean?

Outrunner when i go and check the screen resolution it does not come up with the screen res that i asked for, which was 1600x1200.

It says that the res is  1024x768

did i do something wrong. It came up with the screen res and offered me about half a dozen of them. Then i restarted.

---

### Post by bullraiser on 2007-04-27
Hi,

Even I was having lot of trouble changing the resolution from 1028x800 but I couldnt. 
Almost everyone advises to change the xorg.conf or install nvidia-glx, which eventhough set, is not working.

Have a look onto these threads:

[http://ubuntuforums.org/showthread.php?t=417716&page=3](http://ubuntuforums.org/showthread.php?t=417716&page=3)

[http://ubuntuforums.org/showthread.php?t=419164&page=2&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=419164&page=2&highlight=nvidia)

This should provide some insights.
However, I couldnt still able to find a solution to change my resolution over 1280x800.

My Thread: [http://ubuntuforums.org/showthread.php?t=410861](http://ubuntuforums.org/showthread.php?t=410861)

If anychance, you have luck in getting this done, do let us know.

Cheers--

---

