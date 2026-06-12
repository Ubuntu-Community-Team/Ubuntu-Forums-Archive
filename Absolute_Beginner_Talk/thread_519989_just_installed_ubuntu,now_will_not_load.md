---
title: "just installed ubuntu,now will not load"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by nikef on 2007-08-07
just installed ubuntu
the instalation went fine,but when i reboot i get the cream background and the timer going round and round for ages,tried rebooting several times,what am /have i done wrong ? :(


[COLOR="Red"]please note this has been fixed i now have ubuntu running ,thanks [/COLOR]

---

### Post by nikef on 2007-08-07
ok,its just asked for username and password,its very slow :(

---

### Post by overdrank on 2007-08-07
> **nikef said:**
> ok,its just asked for username and password,its very slow :(

HI could you give some specs on your system? You can use the```
 lspci 
```command in the terminal located under applications, accessories, terminal and post the output here.

---

### Post by nikef on 2007-08-07
hi thanks i will drag my other post up for you 2 read

---

### Post by overdrank on 2007-08-07
> **nikef said:**
> hi thanks i will drag my other post up for you 2 read

Got it yes with that memory it will run slow. Good luck!

---

### Post by nikef on 2007-08-07
please look for my other post

hi,newbie here,will ubuntu fit on this pc

now i have a cream background and a white squared box,in left top hand corner,the ubuntu splash screan came on the the sounds breaking up,it worked perfect on live cd

---

### Post by nikef on 2007-08-07
its a clean install,no windows  :(

---

### Post by nikef on 2007-08-07
here is the specs of the pc 

processor 750 megahertz
128 kb primary memory cache
64 kb secondary memory cache
40 gb usable hard drive
26.32 gb hard drive free space

ADAPI dvd - rom 16x [cd-rom]
samsung cd rom
floppy disc

installed memory
368 mb

display
sis 300/305/630/540/730 [ display adaptor]
maxdata 12.9 [monitor]
multimedia
sis 7018 audio driver
standard game port
internet acsess would be a belkin wireless adaptor

---

### Post by bdann on 2007-08-07
I just installed Ubuntu on my system with the same results.  The only thing I have in common with your system specs is the Belkin wlan adapter.  I removed this, rebooted...came right up.  I plugged in a few other usb devices, they all work fine.  If I wait until the system comes up and insert the Belkin adapter, the system freezes.  So now I'm left with trying to figure out why the heck this is happening...

any tips are appreciated...

---

### Post by ubromtoo on 2007-08-07
Nikef :

    You might try this ( it worked for me ) :

  system> Administration > Login Window > Accessibility

  then UNcheck the box for "enable accessible login"


               hope it works !

---

### Post by nikef on 2007-08-08
> **bdann said:**
> I just installed Ubuntu on my system with the same results.  The only thing I have in common with your system specs is the Belkin wlan adapter.  I removed this, rebooted...came right up.  I plugged in a few other usb devices, they all work fine.  If I wait until the system comes up and insert the Belkin adapter, the system freezes.  So now I'm left with trying to figure out why the heck this is happening...

any tips are appreciated...

Hi and thanks,yes i done that this mornig,and now i am using ubuntu :)

---

### Post by nikef on 2007-08-08
> **ubromtoo said:**
> Nikef :

    You might try this ( it worked for me ) :

  system> Administration > Login Window > Accessibility

  then UNcheck the box for "enable accessible login"


               hope it works !

hey ubromtoo
i manage to get ubuntu up and running,i took out the belkin wireless adaptor and the os loaded lovely

maybe i need new drivers for this,i dont know

---

### Post by nikef on 2007-08-08
> **bdann said:**
> I just installed Ubuntu on my system with the same results.  The only thing I have in common with your system specs is the Belkin wlan adapter.  I removed this, rebooted...came right up.  I plugged in a few other usb devices, they all work fine.  If I wait until the system comes up and insert the Belkin adapter, the system freezes.  So now I'm left with trying to figure out why the heck this is happening...

any tips are appreciated...

bdann do you have internet acess with the belkin router ?

---

### Post by bdann on 2007-08-08
No, I do not have a Belkin router.  I was not able to get the Belkin WLAN adapter to work using the provided modules.  Not able to download and compile new ones because no internet access on the box. Very frustrating. 

I'm going to try to find a different adapter to use.  I read somewhere that the Realtek RTL8185L chipset was pretty well supported under Linux and generic PCI WLAN adapters using this chipset are pretty easy to find for under $20.  

Only other option is to move my router into the room with the Ubuntu PC, which I do not want to do.  (have to run cable, etc)

If I find an adapter that works out of the box with 7.04, I'll post here.

---

### Post by nikef on 2007-08-08
> **bdann said:**
> No, I do not have a Belkin router.  I was not able to get the Belkin WLAN adapter to work using the provided modules.  Not able to download and compile new ones because no internet access on the box. Very frustrating. 

I'm going to try to find a different adapter to use.  I read somewhere that the Realtek RTL8185L chipset was pretty well supported under Linux and generic PCI WLAN adapters using this chipset are pretty easy to find for under $20.  

Only other option is to move my router into the room with the Ubuntu PC, which I do not want to do.  (have to run cable, etc)

If I find an adapter that works out of the box with 7.04, I'll post here.

hey thanks for that ,this belkin adaptor is doing my head in  ](*,),i cant use wired as theres no ethernet at back of pc
will google the Realtek adaptor see if theres anywhere to buy one from,will let you know if i find one

---

### Post by bdann on 2007-08-08
nikef - 

I FINALLY got my Belkin adapter to work using the instructions in this post:

[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

I followed the instructions exactly and now it works perfectly, I'm typing this from my Ubuntu box, connected to my WLAN!  HOOORAAAY!  

Let me know if you have any trouble, the only problem I had was downloading the drivers from serialmonkey.  Not sure what was up, but the file was corrupted initially.  I could not read it from Windows or Linux.  After about an hour I tried downloading again (for the 5th or 6th time) and it worked.  

My results differed slightly from the instructions in that the interface came up as wlan1 instead of wlan0.  Other than that, all is well.  Good luck!

---

### Post by nikef on 2007-08-09
> **bdann said:**
> nikef - 

I FINALLY got my Belkin adapter to work using the instructions in this post:

[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

I followed the instructions exactly and now it works perfectly, I'm typing this from my Ubuntu box, connected to my WLAN!  HOOORAAAY!  

Let me know if you have any trouble, the only problem I had was downloading the drivers from serialmonkey.  Not sure what was up, but the file was corrupted initially.  I could not read it from Windows or Linux.  After about an hour I tried downloading again (for the 5th or 6th time) and it worked.  

My results differed slightly from the instructions in that the interface came up as wlan1 instead of wlan0.  Other than that, all is well.  Good luck!

hey thanks for this
i have just downloaded drivers to the flash disc
put it on the ubuntu pc,now  in the instructions it tells me to copy the file to the home directory
where do i find this,is it called home folder ?
also do i need to open it,extract it ? thanks

---

### Post by nikef on 2007-08-09
Hmmmmmmmmmm
i wish the instructions was a bit more clear :(

---

### Post by bdann on 2007-08-10
Your home directory should be easy to find.  Just click on "Places" on the top toolbar and there's a link to your home directory.  Copy the tar file there, you can just drag and drop it into the folder.  

Then continue with the instructions:

sudo cp home/user/rt73-cvs-daily.tar.gz /usr/src

"user" in this case is the name of your home directory.  My user name is bdann, so mine would be: /home/bdann.  Yours will obviously be different.  

When you get to step #6, if you don't have internet access on the box, you'll need to step down to the bottom where it says **"If you have no other method of internet access on your Linux installation"** and follow those instructions.  Then just jump back up to #7 and continue.  Good luck and don't give up because and it **can** be done and you'll have learned something about linux when you're finished.

---

