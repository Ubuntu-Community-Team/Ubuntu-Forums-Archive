---
title: "Can I install nvidia's driver myself like this -"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by mikex on 2007-08-13
OK, I'm trying to learn here. I got with a guy at work where we run another linux distributuion. He showed me that he could just download nvidia's linux display driver, go into terminal mode, and type sh "driver file name" and it asked a few questions and installed itself, voila. re-booted and it came up with the new driver. Simple enough. I can do that.

Since I am having a few issues with the nvidia driver under Ubuntu, can I not do this myself on Ubuntu, it seemed very simple. If not, can anyone explain why not, and if there is another way to try the driver, can you explain how?

---

### Post by Hobo Joe on 2007-08-13
Yes you can, however, I would recommend using Envy, it's easier and more thorough, and less likely to mess up.

See my sig for a link.

---

### Post by V3lier on 2007-08-13
> **Hobo Joe said:**
> Yes you can, however, I would recommend using Envy, it's easier and more thorough, and less likely to mess up.

See my sig for a link.
Me too. I had problems installing NVidia myself but Envy did everything. Works extremely well :D!

---

### Post by mikex on 2007-08-13
> **Hobo Joe said:**
> Yes you can, however, I would recommend using Envy, it's easier and more thorough, and less likely to mess up.

See my sig for a link.

Thanks for responding. Can you expound on "mess up"? What is going to go wrong with the process when I use the manufacturers installation program? I watched it firsthand and it just "worked" on another linux distro. Is there something about Ubuntu that is, for lack of a better term, proprietary that would cause it to mess up. I'm not sure what you mean by that in terms of your answer.

---

### Post by bodhi.zazen on 2007-08-13
You can do either (envy or directly)

I install the nvidia driver myself (manually) although envy is a fine script.

You will need to install build-essential and your kernel headers first, then run the nvidia script (you will need to drop out of X).

You will need to run the nvidia script with each kernel update as well.

The envy script can be run in X and some feel this is easier.

---

### Post by johnl on 2007-08-13
Hi,

There are a couple problems you might run into when installing the NVIDIA driver using their installer.

First, whenever your kernel is upgraded, the next time you reboot the nvidia kernel module will fail to load, dump you to the terminal, and you will have to reinstall the nvidia driver again (since it must build the module for the current kernel).

Second, it's possible that it might conflict with the driver that is installed via Ubuntu's repos.  In this case, you'll also be dumped to a terminal and you'll have to figure out what the problem is and fix it -- usually you'll see a mismatch between the nvidia kernel module version and the nvidia driver.

Finally, you have to go back to their website and re-download the file and re-install it when a new version comes out.

The advantages to using the packaged ubuntu version are:

When you upgrade your kernel, the nvidia driver is automatically upgraded along side it.  

New versions of the module can be pushed out to you directly and installed.


Basically, I would recommend using the ubuntu version.  It's easier and less likely to cause problems for you.  If you're having problems installing it, post back and I or someone else can probably help you.


Hope this helps!

---

### Post by Hobo Joe on 2007-08-13
> **mikex said:**
> Thanks for responding. Can you expound on "mess up"? What is going to go wrong with the process when I use the manufacturers installation program? I watched it firsthand and it just "worked" on another linux distro. Is there something about Ubuntu that is, for lack of a better term, proprietary that would cause it to mess up. I'm not sure what you mean by that in terms of your answer.

Well, I guess 'mess up' wasn't the best way to put it. Because it doesn't necessarily mess up, but rather things don't work properly, and I think Envy does a better job configuring the xorg.conf file. Also, Envy has a really good uninstall script incase things do go wrong, and it even works in text mode, incase you can't boot into the xserver.

---

### Post by mikex on 2007-08-13
> **bodhi.zazen said:**
> You can do either (envy or directly)

I install the nvidia driver myself (manually) although envy is a fine script.

You will need to install build-essential and your kernel headers first, then run the nvidia script (you will need to drop out of X).

OK, where are "build-essential and your kernel headers"? Is that an item that I can get Ubuntu to get for me somehow. These are the types of questions I know you experts don't even think twice about, but I have no clue what to do about "install build-essential and your kernel headers first" I don't know how to proceed even with that helpful suggestion.

:(

---

### Post by Hobo Joe on 2007-08-13
> **mikex said:**
> OK, where are "build-essential and your kernel headers"? Is that an item that I can get Ubuntu to get for me somehow. These are the types of questions I know you experts don't even think twice about, but I have no clue what to do about "install build-essential and your kernel headers first" I don't know how to proceed even with that helpful suggestion.

:(

This is why Envy is so nice. :)


Also, I forgot to mention, but like johnl said, nVidia drivers break everytime there is a kernel update, which is where Envy comes in. All you have to do is run in recovery mode and reinstall nvidia drivers, but manually, you have to find the download, and then try and remember all the commands and filenames.

---

### Post by mikex on 2007-08-13
> **Hobo Joe said:**
> This is why Envy is so nice. :)


Also, I forgot to mention, but like johnl said, nVidia drivers break everytime there is a kernel update, which is where Envy comes in. All you have to do is run in recovery mode and reinstall nvidia drivers, but manually, you have to find the download, and then try and remember all the commands and filenames.

OK thanks, then the way to go is get "Envy" and follow the instructions. Is it that simple, or are there more surprises to intrigue me in that process?

---

### Post by bodhi.zazen on 2007-08-13
There are instructions for Envy here: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

And the Nvidia drivers here : [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by Hobo Joe on 2007-08-13
Nope, it's all very straightforward, all you do is download the package(it will install automatically), then run it, and select Install nVidia driver. Then just make sure you let it config your xorg for you, and that's it!

If you want to run it in recovery mode, then just type
```

envy -t

```

---

### Post by stchman on 2007-08-13
> **mikex said:**
> OK, I'm trying to learn here. I got with a guy at work where we run another linux distributuion. He showed me that he could just download nvidia's linux display driver, go into terminal mode, and type sh "driver file name" and it asked a few questions and installed itself, voila. re-booted and it came up with the new driver. Simple enough. I can do that.

Since I am having a few issues with the nvidia driver under Ubuntu, can I not do this myself on Ubuntu, it seemed very simple. If not, can anyone explain why not, and if there is another way to try the driver, can you explain how?

If you are running Feisty it is easiest to just enable the restricted driver.

---

### Post by mikex on 2007-08-13
> **stchman said:**
> If you are running Feisty it is easiest to just enable the restricted driver.


That's what it says I am using right now. When I sudo whateverthepathwas/nvidia-settings and change the resolution, all terminal windows are pure white after that and nothing will fix it so far unless I go back to the previous resolution (1024x768) and restart.

#-o

---

### Post by stchman on 2007-08-14
> **mikex said:**
> That's what it says I am using right now. When I sudo whateverthepathwas/nvidia-settings and change the resolution, all terminal windows are pure white after that and nothing will fix it so far unless I go back to the previous resolution (1024x768) and restart.

#-o

I had the same difficulty.  I just edited my xorg.conf file and inserted "1280x1024" as the first resolution in the line of resolutions.

---

