---
title: "problem Nvidia FX 5200 series on ubuntu 7.10"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by gladrock on 2008-02-28
could anyone please help me out i installed yesterday Ubuntu 7.10 on my machine
but my video is not  working properly so i need to install the nvidia drivers
but since i am a noooooooooob on Linux how do i do this can some one help me please
i appreciate sorry for my bad English

---

### Post by overdrank on 2008-02-28
> **gladrock said:**
> could anyone please help me out i installed yesterday Ubuntu 7.10 on my machine
but my video is not  working properly so i need to install the nvidia drivers
but since i am a noooooooooob on Linux how do i do this can some one help me please
i appreciate sorry for my bad English

HI and welcome, have you tried the restricted drivers located under system, administration?

---

### Post by bumanie on 2008-02-28
Try what overdrank suggests. If that doesn't work (that is a fairly old card), you will have to go to the nvidia linux site and download a driver. It is likely the driver you need will be called a legacy driver. You will then have to install it in console. If restricted drivers doesn't work post back and I or someone else will supply full instructions. It's a bit involved that's why i won't confuse things with instructions if the restricted drivers method works.

---

### Post by gladrock on 2008-02-28
well i tryed the restricted drivers and when i try to enable it it gives me an message
saying the software source for this package nvidia-glx-new is not enabled

what do i do next i dont see the legacy driver to download could you help me with a link pls i apreciate

---

### Post by bumanie on 2008-02-28
i would've thought you would need an  earlier driver, but a geforce fx 5 series card seems to be covered here [http://www.nvidia.com/object/linux_display_ia32_169.12.html](http://www.nvidia.com/object/linux_display_ia32_169.12.html) You can check yourself by going here and entering your card specs [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Download to desktop and follow these instructions.

Stop xserver ctrl-alt-F1 together
enter username and password
> sudo /etc/init.d/gdm stop
--> hit enter
> sudo cd ~/Desktop
--> hit enter
> sh NVIDIA-Linux-x86-169.12.pkg1.run
--> hit enter 
> sudo /etc/init.d/gdm start
--> hit enter
If gui doesn't start either sudo reboot or try ctrl-alt-F7
Hope this works for you. It did for me.

---

### Post by gladrock on 2008-02-28
ty very mutch trying it right now i will reply with results thanks
Could not open the file /home/jomar/Desktop/NVID&#8230;Linux-x86-169.12-pkg1.run using the Western (ISO-8859-15) character coding.
i am getin a error message when i try to run it under the ctrl alt f1 comand
its saying canot open the file

---

### Post by gladrock on 2008-02-28
i tryed to run the file and i got a message saying it must run as root

how do i run it as root pls help

---

### Post by bumanie on 2008-02-28
Sorry, my mistake. The line starting with sh ... should be 
> sudo sh NVIDIA-Linux-x86-169.12.pkg1.run
The rest should work OK. I think all the syntax is correct.

---

### Post by gladrock on 2008-02-28
you had it right i got started and got an error saying i needed to install a LIBC something

not sure what it is

---

### Post by bumanie on 2008-02-28
That is most likely a library file (roughly equivalent to a dll in windows). Get the exact name and then type the name into Search in synaptic. If it comes up in synaptic click on it and mark it for installation. If it is not there put the file name into the search bar of a search engine and hopefully you will find it that way.
I think it may be libc5++ or something, but due a non-functioing new computer which is back where I bought it getting tested, I'm on windows and can't help much more. Hope everything works out. You should be able to fnd the libc file somewhere. Once you have that (unless another dependency is missing) the former instructions should work. I'm off to bed now -nearly 2 a.m. here. Good luck.

---

### Post by gladrock on 2008-02-28
> **bumanie said:**
> That is most likely a library file (roughly equivalent to a dll in windows). Get the exact name and then type the name into Search in synaptic. If it comes up in synaptic click on it and mark it for installation. If it is not there put the file name into the search bar of a search engine and hopefully you will find it that way.
I think it may be libc5++ or something, but due a non-functioing new computer which is back where I bought it getting tested, I'm on windows and can't help much more. Hope everything works out. You should be able to fnd the libc file somewhere. Once you have that (unless another dependency is missing) the former instructions should work. I'm off to bed now -nearly 2 a.m. here. Good luck.

its up and running thank bro for your patience and help really apreciate

---

### Post by int86 on 2008-03-06
> **bumanie said:**
> i would've thought you would need an  earlier driver, but a geforce fx 5 series card seems to be covered here [http://www.nvidia.com/object/linux_display_ia32_169.12.html](http://www.nvidia.com/object/linux_display_ia32_169.12.html) You can check yourself by going here and entering your card specs [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Download to desktop and follow these instructions.

Stop xserver ctrl-alt-F1 together
enter username and password

--> hit enter

--> hit enter

--> hit enter 

--> hit enter
If gui doesn't start either sudo reboot or try ctrl-alt-F7
Hope this works for you. It did for me.

Sould the above procedure be done while display is on grapics card or on onboard .
I have got exactly same problem. Installation works fine with onboard graphics but booting hangs while graphics card is enabled. I have same card.

---

