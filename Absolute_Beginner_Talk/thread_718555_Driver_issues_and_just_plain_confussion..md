---
title: "Driver issues and just plain confussion."
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by shellback84 on 2008-03-08
Hello everyone, I am shellback84 and I have many questions but I will start with two and go from there. First, to give you a clear understanding how raw I am at this OS I did not know what the terminal was when I was reading another thread here at Ubuntu's basic beginner forums. Yes I figured it out but I want you to have an incite as to how unfamiliar I am with this sort of OS. Anyway, Like one of the posters here I am having problems connecting on the internet. But unlike that person I am able to type in my wireless code and get on, as it it obvious because I am here now. The problem is the program that is making the connection keeps defaulting to 128 bit and my wireless modem is 64. So each time I come here to Ubuntu to play I must type in the code first and I have tried many times to log off and save this input, with no joy. Any ideas?

My next question addresses my brand new GeForce video card. I have a 8800 GTS and so far non of the drivers I have tried are working. After entering the command: lspci -v it states that my card is an unknown EVGA video card. Does this mean I am doomed till a driver is released for my video card or worse an updated to Ubuntu is released? Thanks for any help.

---

### Post by mikeyphi on 2008-03-08
Hi there!!

Your second question first!! Go here for the new video driver: [http://linux.softpedia.com/get/System/Hardware/nVidia-Linux-Display-Driver-IA32-17977.shtml](http://linux.softpedia.com/get/System/Hardware/nVidia-Linux-Display-Driver-IA32-17977.shtml)

Ask again if you have problems following the instructions - but they are minimal!

To your first question - please post which program you mean when talking about making the connection. And in which program do you input your wireless security code?

---

### Post by Hospadar on 2008-03-08
How did you install/enable your video drivers? Did you use the restricted drivers manager in System->Administration?  If not, try that and see if it works.

If that's what you've already tried, or it doesn't work, your best bet would be to use the envy scripts.  They are a package of scripts that make configuring and installing of video drivers waaay easier.
get it [here]("http://www.albertomilone.com/nvidia_scripts1.html"), and [here]("http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu") is how to install it.

Once you've installed it, you'll have to run it in text mode, so jump over to a terminal (Ctrl-Alt-F1) log in, and type ```
sudo envy -t
```then I would do the "remove nvidia drivers" and the "clean nvidia drivers" options before you  do the "install nvidia drivers options"
It'll ask you a couple times if it can do certain things (edit some files, restart your X server, and you should let it do those things)

Ideally now your video will be working

As for your wifi, do you know your wifi reciever's chipset? (you might be able to find it in lspci, or lsusb if it's a usb adapter)  Alternatively, if it keeps switching to 128 bit, can you just set your wifi router to 128 bit?

EDIT: Also note, envy installs basically the same drivers as listed above, it just does all the hard work for you in terms of configuration.

---

