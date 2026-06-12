---
title: "Ubuntu Freezes on desktop load"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by weightgain4000 on 2007-03-05
Hello,

Im having some problems with Ubuntu 

Im new to Linux however I have had some past experience trying it out, only to get frustrated and go back to windoze.............

anyway installed Ubuntu 6.10 AMD64 version updated system then decided to install Beryl using this guide 

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29)

Beryl installed ok and worked, however I changed some settings in the Beryl manager and gnome froze! I  rebooted and still have same problem

is there a "safe mode" I can boot to so can change the settings back to what they where or uninstall beryl, or prevent it from loading on start up? if so what do I do?

I had a search on google but I must have not been using the correct terms :p 

Any help is greatly appreciated

Thanks

John

---

### Post by PartisanEntity on 2007-03-05
Yes there is a safe mode, it should be one of the options in the boot loader. Do you see the boot loader when you start your machine?

Edit: It's called recovery mode, see screen shot:
[http://www.pcentraide.com/tutoriel/dual-boot/dual-boot-linux-windows-7.jpg](http://www.pcentraide.com/tutoriel/dual-boot/dual-boot-linux-windows-7.jpg)

---

### Post by weightgain4000 on 2007-03-05
no,

it just starts like normal but hangs at desktop

---

### Post by weightgain4000 on 2007-03-05
sorry my bad,

I'll try the boot loader :oops:

---

### Post by PartisanEntity on 2007-03-05
Ignore this, I posted it while you were replying.

---

### Post by weightgain4000 on 2007-03-05
ok great! im in the recovery mode, 

I set beryl manager to commence on startup 

How do I disable this? 

Thanks

John

---

### Post by PartisanEntity on 2007-03-05
If you don't want beryl to load at start up then go to System > Preferences > Sessions. Click on the Startup Programs tab and delete the entries for *beryl-manager* and *emerald --replace*.

I am not 100% sure of this though.

---

### Post by weightgain4000 on 2007-03-05
Just had a look, those entrys are not there :p would they be written to a config file anywhere?

---

### Post by PartisanEntity on 2007-03-05
hmm I'm afraid that's as far as I can help you, although I use beryl from time to time I am not too familiar with it beyond basics.

---

### Post by weightgain4000 on 2007-03-05
no worries

Thanks for the help anyway :)

---

### Post by weightgain4000 on 2007-03-06
Can anyone offer any other suggestions? Im still stuck with my beryl problem :P

Thanks

John

---

### Post by Corvo78 on 2007-03-06
I had Beryl freeze up on me too (during every startup).
In my case this was related to activating the 'Blur'-plugin.
I simply booted into the 'recovery console' and started looking for a settings file.

If I'm not mistaken...:
Beryl stores its' settings in your home folder under".beryl". So:
```
/home/weightgain4000/.beryl/
```
There should also be a file named settings or some such.
I used a text editor (**nano**) and opened the file and searched for an entry about the 'Blur'-plugin.
I was lucky (to find an entry) and managed to disable the plugin.

After that I could safely reboot back into my Ubuntu system and enjoy Beryl (only without the Blur).


*(Sorry I can't tell you exactly which folder and file to edit, but I can't access any Ubuntu install at the moment)*
Hope this little story can be of help to you!

---

### Post by weightgain4000 on 2007-03-06
Hey, 

Thanks for the post

Logged into IRC and got some help from the folks in there :-D

---

### Post by PartisanEntity on 2007-03-06
Glad to hear that, if you found a solution please post it here for others and mark your **initial post** of this thread as solved :) (you will have to click on edit and then advanced edit then tick 'resolved')

---

