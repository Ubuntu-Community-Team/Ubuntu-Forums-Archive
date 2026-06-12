---
title: "New computer = New problems"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by GeorgiaBoot on 2008-03-02
I just got my new computer and I am now having problems with my display.

I am booting into Ubuntu 7.10 via a USB Hard Drive.

My old computer had an atix300 graphics card and everything was setup fine.

Now the new computer I am booting into has the nvidia 8800gt card. My monitor is a 24' wide screen.

How do I get it to display resolutions higher than 800x600? Or how do I re-configure my display setting again?

The res I want is 1920x1200.

Thanks for the help.

---

### Post by Tatty on 2008-03-02
Have you installed the drivers for your card?

Go to System->Administration->Restricted Drivers Manager

---

### Post by GeorgiaBoot on 2008-03-02
I went there and it said "your computer does not need any restricted drivers"

What now?

Thanks

---

### Post by Tatty on 2008-03-02
After that try the multipe monitor setup dialog - i cant remember which menu it is in (not on ubuntu atm im afraid), but its either preferences or administration.

---

### Post by Tatty on 2008-03-02
Have you tried manually installing the driver from the Nvidia website?

[http://ubuntuforums.org/showthread.php?t=699964]("http://ubuntuforums.org/showthread.php?t=699964")

---

### Post by GeorgiaBoot on 2008-03-02
I have gone to "screens and graphics" and gone to video card but when I select the 8series it gives some funny named driver that I don't think is right. I have gone to every screen thing I can find and I am still stuck with 800x600.

How can I get it to recognize my graphics card? I think the driver it is recognizing is some generic nvida driver.

---

### Post by GeorgiaBoot on 2008-03-02
I am right now downloading it and I will see if that works, let yu know in a bit.

Thanks

---

### Post by GeorgiaBoot on 2008-03-02
I downloaded it but I am stuck on how to install? I have no clue! Here is where I am following the directions but when I go and paste the thing they said to do in the terminal is does nothing.

[http://www.nvidia.com/object/linux_display_ia32_169.12.html](http://www.nvidia.com/object/linux_display_ia32_169.12.html)

---

### Post by Tatty on 2008-03-02
[https://help.ubuntu.com/community/RestrictedDrivers/NVIDIAOfficial?highlight=%28nvidia%29](https://help.ubuntu.com/community/RestrictedDrivers/NVIDIAOfficial?highlight=%28nvidia%29)

try this

---

### Post by GeorgiaBoot on 2008-03-02
I tried that and A) it was very confusing B) once I got everything written down and followed the steps to a tee it did not work, just messed things up worse.


Is there any simple way to get this done? I mean in windows I clicked download>install and I was done.

Not having to go edit files is nice....

Thanks

---

### Post by Tatty on 2008-03-02
well what happened when you tried to install it?

---

### Post by GeorgiaBoot on 2008-03-02
I think it was something like Bash command not able or something like that.

I followed everything exactly....

Is there No other way?

---

### Post by Tatty on 2008-03-02
There may be another way, but I have never installed the proprietry Nvidia drivers myself so i cant help you.

It sounds like you probably made a typo or something... can you copy and paste exactly what comes up?

---

### Post by GeorgiaBoot on 2008-03-02
I can't because in the instructions, it says kill the xfile or something and when I do that in command prompt it takes me to a black screen and I can't get out of that.


I mean this should be such a simple thing to do but of course Linux has to make it complicated...


[https://help.ubuntu.com/community/RestrictedDrivers/NVIDIAOfficial?highlight=%28nvidia%29](https://help.ubuntu.com/community/RestrictedDrivers/NVIDIAOfficial?highlight=%28nvidia%29)

---

### Post by Tatty on 2008-03-02
> **GeorgiaBoot said:**
> I can't because in the instructions, it says kill the xfile or something and when I do that in command prompt it takes me to a black screen and I can't get out of that.


I mean this should be such a simple thing to do but of course Linux has to make it complicated...


[https://help.ubuntu.com/community/RestrictedDrivers/NVIDIAOfficial?highlight=%28nvidia%29](https://help.ubuntu.com/community/RestrictedDrivers/NVIDIAOfficial?highlight=%28nvidia%29)

Nope, it is Nvidia who make it complicated.

---

### Post by GeorgiaBoot on 2008-03-02
I downloaded the nvidia driver then they say type "sh NVIDIA-Linux-x86-169.12-pkg1.run" to install the driver. When I do this pops up "sh: Can't open NVIDIA-Linux-x86-169.12-pkg1.run"


Would doing a complete re-install fix it?

---

### Post by Tatty on 2008-03-02
you will need to run it as sudo as it require root privilages:

```
sudoi sh NVIDIA-Linux-x86-169.12-pkg1.run
```


There is a thread here from the other day of someone who was trying to install the same card:

[http://ubuntuforums.org/showthread.php?t=711499]("http://ubuntuforums.org/showthread.php?t=711499")

perhaps you want to try Envy (mentioned in that thread)

---

### Post by danielcc on 2008-03-02
i bet you can force your display settings in xorg

---

### Post by xeth_delta on 2008-03-02
> **GeorgiaBoot said:**
> I downloaded the nvidia driver then they say type "sh NVIDIA-Linux-x86-169.12-pkg1.run" to install the driver. When I do this pops up "sh: Can't open NVIDIA-Linux-x86-169.12-pkg1.run"


Would doing a complete re-install fix it?

You have to do that with administrative privileges. Precede the call you mentioned by "sudo". If the nvidia script is not executable, do the following:

```
chmod +x NVIDIA-Linux-x86-169.12-pkg1.run
```

---

### Post by GeorgiaBoot on 2008-03-02
The chmod line did not work before the sudo line.

I used envy and that worked, but I had to go edit xforg file.

Thanks for the help even though I am frustrated! :)

What are the downsides of using envy?

Thanks

---

### Post by xeth_delta on 2008-03-02
> **GeorgiaBoot said:**
> The chmod line did not work before the sudo line.

I used envy and that worked, but I had to go edit xforg file.

Thanks for the help even though I am frustrated! :)

What are the downsides of using envy?

Thanks

So, did it work in the end with Envy? I don't know what the downsides of using ENVY would be, since I don't have an nVidia card on my laptop, but a lot of people actually recommend it.

nVidia card owners, any opinioins pro/against using ENVY?

---

### Post by GeorgiaBoot on 2008-03-03
Yes, it did work.

I had just read something that when you upgrade to the latest OS from Ubuntu that there were problems with it. Who knows I guess!

---

