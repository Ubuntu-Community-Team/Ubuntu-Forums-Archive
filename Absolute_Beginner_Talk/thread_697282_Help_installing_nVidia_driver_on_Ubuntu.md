---
title: "Help installing nVidia driver on Ubuntu"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by raulhmacias on 2008-02-15
Long story short: I installed Ubuntu on a Dell Latitude D800 and now I want to install the nVidia driver.

I've already downloaded the driver which is a file called 'NVIDIA-Linux-x86-96.43.05-pkg1.run'
Now, according to the [instructions]("http://us.download.nvidia.com/XFree86/Linux-x86/96.43.05/README/README.txt") , I should "exit the X server and kill all OpenGL applications " and also "set the default
run level on your system such that it will boot to a VGA console and not
directly to X."

After that I am supposed to type the following somewhere:

    # cd yourdirectory
    # sh NVIDIA-Linux-x86-96.43.05-pkg#.run

Problem is, after being a Windows user all my life, I don't know what X server is nor how to change the default run level.

Is there a step-by-step somewhere on how to do this for new Linux users? Please be merciful and help me! ](*,)

---

### Post by Tatty on 2008-02-15
It would probably be best for you to install the nvidia driver from the repositories rather than downloaded from a website.
Go into the restricted drivers manager and see if that gives you some drivers you can install.

It might be a good idea for you to have a read of this guide on how to install things in ubuntu [https://help.ubuntu.com/7.10/add-applications/C/index.html]("https://help.ubuntu.com/7.10/add-applications/C/index.html")
Its always best to stick with installing things from the repositories if you can, that way ubuntu can look after all your installs for you.

That "somewhere" that you have to type those commands into is the Terminal  Applications->Accessories->Terminal.  As a linux user, you will soon learn to love the terminal :)

**EDIT:** You might also want to read this guide on installing the proprietry Nvidia drivers on Ubuntu: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

---

### Post by oedha on 2008-02-15
you can press : ctrl+alt+F2
then type : sudo /etc/init.d/gdm stop
then you can do sudo sh NVIDIA.........
i think it can be done in terminal from application - accesories -terminal
and type : sudo sh NVIDIA........

---

### Post by raulhmacias on 2008-02-15
thx! I'll give it a try

what about changing the "default run level"? where or how do I do that?

thx again

---

### Post by raulhmacias on 2008-02-15
> **Tatty said:**
> It would probably be best for you to install the nvidia driver from the repositories rather than downloaded from a website.
Go into the restricted drivers manager and see if that gives you some drivers you can install.

It might be a good idea for you to have a read of this guide on how to install things in ubuntu [https://help.ubuntu.com/7.10/add-applications/C/index.html]("https://help.ubuntu.com/7.10/add-applications/C/index.html")
Its always best to stick with installing things from the repositories if you can, that way ubuntu can look after all your installs for you.

That "somewhere" that you have to type those commands into is the Terminal  Applications->Accessories->Terminal.  As a linux user, you will soon learn to love the terminal :)

**EDIT:** You might also want to read this guide on installing the proprietry Nvidia drivers on Ubuntu: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

wow! that was quick! I definetely will read that guide. thx for your help.:)

---

### Post by Tatty on 2008-02-15
Just found this for you, tells you how to do what you are trying to do step by step.  But again, i recomend installing via the restricted drivers manager unless you really want the latest drivers :)

[https://help.ubuntu.com/community/RestrictedDrivers/NVIDIAOfficial?highlight=%28nvidia%29]("https://help.ubuntu.com/community/RestrictedDrivers/NVIDIAOfficial?highlight=%28nvidia%29")

---

### Post by Phulerock on 2008-02-15
Tatty's solution is good for you

---

### Post by raulhmacias on 2008-02-15
> **oedha said:**
> 
 type : sudo /etc/init.d/gdm stop


I suppose that's the part about the 'default run level' ?:confused:

---

### Post by raulhmacias on 2008-02-15
> **Tatty said:**
> Just found this for you, tells you how to do what you are trying to do step by step.  But again, i recomend installing via the restricted drivers manager unless you really want the latest drivers :)

[https://help.ubuntu.com/community/RestrictedDrivers/NVIDIAOfficial?highlight=%28nvidia%29]("https://help.ubuntu.com/community/RestrictedDrivers/NVIDIAOfficial?highlight=%28nvidia%29")

Great! Thanks a lot guys.:)

---

### Post by oedha on 2008-02-15
i just know that.....to shutdown the desktop after that you can turn it on again with almost the same syntax......replace stop with start
actually...there is init thing....i forgot...init 3 maybe :( :)

---

### Post by raulhmacias on 2008-02-15
By the way: I am trying to install the nVidia driver to get the best resolution for my display:
# 1920x1200 WUXGA active-TFT panel
# 32MB Nvidia Geforce4 4200 Go graphics

right now, all I get is up to 1280x800 :(

---

