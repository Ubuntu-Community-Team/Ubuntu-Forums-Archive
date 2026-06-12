---
title: "When  all else fails?!?! Who to turn to?!?!"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by S15_88 on 2007-06-21
Hi there I have made several posts in the beginner talk forum and the networking forum related to my wireless problem i got great feedback but now i've encountered a problem that noone has yet to be able to help me with.  I am wondering if there is a forum for advanced questions or an emergency forum for when all else fails?  as far as i'm concerned the beginner talk gives u the most feedback.  So now that i have gotten all this help but now noone knows wat i should do and its got me puzzled who do i turn to?


here is my problem:

i've got an Intel Corporation PRO/Wireless 4965 AGN card, not supported by Ubuntu, so installed ndiswrapper then installed the driver. all went well here is some output for u to reference:
> 
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)

alain@S15:~$ ndiswrapper -l
netw4v32 : driver installed
        device (8086:4229) present


so after all that it should be good, i ran the sudo modprobe ndiswrapper command to activate the wireless card but still nothing:

NO WiFi light
NO Wifi connection listed in the network manager
NO Wifi when ifconfig is done

tried reinstalling everything several times, rebooting, running everycommand possible but still nothing!  Anyone got any ideas?  I know for a fact others with this card got it working with the exact same procedure as i have done, so i know it can work!  If anyone can shed some light on this i would greatly appreciate it!!! 

Thanks for all the help so far, Alain  
ps. if anyone wants more output from the terminal or computer specs let me know.

---

### Post by PartisanEntity on 2007-06-21
please type the following in the terminal and paste the output here:

```
iwconfig
```

---

### Post by S15_88 on 2007-06-21
alain@S15:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.

alain@S15:~$

---

### Post by S15_88 on 2007-06-21
27 views, noone got anythin, come on ppl help a fellow user out!

---

### Post by bren on 2007-06-21
hi S15

you say which wireless card you have but not which computer.

its just possible that you have ACER or AMILO model which need (windows) software switch on of wireless card.     Search for ACPI and wireless or post back if this IS your problem

hope that helps

bren

---

### Post by S15_88 on 2007-06-21
i've got a dell inspiron 640m i'm using the windows drivers with NDISwrapper, my wireless works fine in vista and in ubuntu i ahve a shortcut key and i know it works cause the bluetooth light comes on but no Wifi they're are both accessed with the same shortcut key.

Thanks, Alain

---

### Post by kevinlyfellow on 2007-06-21
Intel does have native (and open) linux drivers for this card
[http://www.intellinuxwireless.org/?p=iwlwifi&n=HOWTO-iwlwifi](http://www.intellinuxwireless.org/?p=iwlwifi&n=HOWTO-iwlwifi)

---

### Post by S15_88 on 2007-06-21
I took a look at that and gave it a try but i got errors at several points, i am more curious as to why the way i chose to do it isn't working.  much simpler and faster than doing the iwlwifi.  with NDISwrapper u jus install that download the windows driver and do modprobe ndiswrapper, from the people i have talked to with the 4965 they have all done it successfully with NDISwrapper, so how come mine isn't working?  it's not neccessary for me to have wireless becuase if i ever need it i just boot into vista, i'm just curious to get it working!

Thanks, Alain

---

### Post by wormser on 2007-06-21
There is a [blog]("http://kuscsik.blogspot.com/2007/06/how-to-install-intel-4965-wireless.html") with directions.  I found the link from this [thread]("http://ubuntuforums.org/showthread.php?t=396204&highlight=4965&page=3").  Also take a look at the 28th post.

---

### Post by renerey on 2007-06-23
s15, 

what version of Ndiswrapper are you using? if you got your ndiswrapper  from apt, i'd suggest you get the latest version from their website. you might wanna try physically turning on or off your wifi (fn+f2). your card might not even be turned on. for my driver, i installed the netw4x32. try installing that version and not the netw4v32.

---

