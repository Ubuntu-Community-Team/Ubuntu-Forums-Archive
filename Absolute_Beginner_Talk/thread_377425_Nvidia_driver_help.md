---
title: "Nvidia driver help"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by fixxlet on 2007-03-06
Hello everyone

I am quite new to Ubuntu.

I have been trying for quite some time now to get openGL to work with my Ubuntu but to no avail. Can someone please help me?

The HOWTO's have lead me nowhere.

Here is my setup:
Ubuntu 6.10 (2.6.17-11-generic)
NVidia Model 64

For starters I have got no idea which driver to download from the Nvidia archives that will work with this card.

Can one get openGL to work with the generic Nvidia drivers ?

Thanks in advance.

Wayne

---

### Post by gh0st on 2007-03-06
Hi,

I don't know much about the card you've got I'm afraid but I found that using Envy was really helpful for me in setting up my Nvidia driver to work with Beryl properly. It's a script that is maintained by Alberto Malone and he does a great job, here is a link to his site: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

It should take a lot of the pain out of the job for you. It will install the latest and best NVidia driver it can, it also works for ATI cards.

Hope that helps, good luck :)

---

### Post by gh0st on 2007-03-06
You could use these commands in the terminal to download and run envy.

```

wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.0-0ubuntu1_all.deb

```

..to get the Deb package

```

sudo dpkg -i  envy_0.9.0-0ubuntu1_all.deb

```

..to install the package

```

envy

```

..To run Envy

Then just use the menu and follow the instructions.

Good luck :)

---

### Post by old_geekster on 2007-03-06
Here is another link to help you install the latest Nvidia drivers:

[http://www.ubuntuforums.org/showthread.php?t=336412&highlight=install+latest+nvidia+drivers](http://www.ubuntuforums.org/showthread.php?t=336412&highlight=install+latest+nvidia+drivers)

This is the one that I use.

---

### Post by windozer on 2007-03-06
Does envy or the other way work for feisty/ubuntu 7?

---

### Post by gh0st on 2007-03-08
I don't think Envy works on Fiesty but I've never tried it. In the requirements section of the Envy site it says you need Dapper or Edgy but it doesn't mention Fiesty at all. That could mean either it doesn't work with Fiesty or that part of the site hasn't been updated since Fiesty came out I dunno. I expect Envy will be updated to work with Fiesty when it's fully released if it doesn't work now.

You would probably need to do some research on Envy to be sure. I don't really know sorry.

I'm sure that's helped you loads...... not  :)  ;) 

Maybe someone smarter will post a follow up.

---

### Post by Bachstelze on 2007-03-08
```

sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install nvidia-glx
sudo nvidia-xconfig
```

Has always worked for me in Edgy, I think it should work in Feisty too.

---

### Post by cryptoD on 2007-03-08
The best way to install Nvidia driver is to use this automatic installation 
[http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/nVIDIA](http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/nVIDIA) 
all what you need to do is to copy/paste the script and run it ! :) 
i've tried it on a fresh Edjy installation , it will install Nvidia driver + beryl . Works 100%

---

### Post by Bachstelze on 2007-03-08
Unless I'm terribly mistaken, he didn't say he wanted to install Beryl...

---

### Post by cryptoD on 2007-03-08
this is the easiest solution for the extreme newbies ! (like me :mrgreen: )

---

### Post by gh0st on 2007-03-08
That script looks quite handy. I might try that next time I do an Edgy install.

It would be handy if you wanted to install Beryl as well, it would be helpful for newbies, a lot of new users only want the 3D driver just to run desktop effects it seems. I am a bit weary of just running shell scripts without knowing much about them normally though. 

Thanks for the heads up :)

---

### Post by djtecha on 2007-03-08
Yea those scripts work fine but it still doesn't allow for true 3d support and when ever I change the xcong file from nv to NVIDIA it totally kills my xserver until I change it back. Any ideas?

---

