---
title: "Can't connect to the Internet"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by aberadam on 2007-05-19
I cannot connect to the Internet via my USB wireless dongle, which is the only way I can.  I'm using XP now, so the connection is working. 

In Ubuntu it shows the correct network (BT HomeHub XXX) and asks for the password.  I enter it and nothing.  Sometimes the icon changes to a swirling icon and it's 'looking for the network key' or something, then it does nothing.  

What can I do next?  Because it shows the wireless network correctly and gives a signal strength presumably that means there's no problem with the drivers for the wireless dongle/card, right?  

Two more questions if you have time: 

1) On the desktop in Ubunti it shows my old 'C partition' for Windows, now called hsa1, how can I get rid of it after I've copied a few files from it?  I don't want 'hsa1' on my desktop.  

2) I have an ATI grapics card.  Whose drivers do I get?  Ones from Ubuntu or ATI?  Have the ones from Ubuntu been modified to work properly 'cause I gather there's a ton of problems with ATI graphics cards. 

Thanks.

---

### Post by Najand on 2007-05-19
Use: System -> Administration -> Network
Then click on your connection and disable roaming... Enter your connetion data there and save it (close it)....
See if it works.... 
1. You can comment the line that has hsa1 in /etc/fstab.... After doing that and rebooting your computer,, it won't apear on your desktop....
2. Probably: fglrx
It is included in Ubuntu Repositories.

---

### Post by aberadam on 2007-05-19
> **Najand said:**
> Use: System -> Administration -> Network
Then click on your connection and disable roaming... Enter your connetion data there and save it (close it)....
See if it works.... 
1. You can comment the line that has hsa1 in /etc/fstab.... After doing that and rebooting your computer,, it won't apear on your desktop....
2. Probably: fglrx
It is included in Ubuntu Repositories.

I have no idea what my 'connection data' is though.  DHP/TCP etc - meaningless.  All I know is the password.  Which is the right one.  

I don't know what 'comment the line' means.  

fglrx?  That's the ATI official drivers right?  And they're included?

---

### Post by Najand on 2007-05-19
You won't need DHP/TCP as far as it can find it automatically using DHCP... You just need to enter your netwrok connection name and the password and then set it to use DHCP....
For fstab:
" Push Alt+F2
* Type: "gksu gedit /etc/fstab"
* Find the filesystem you are looking for.... errr.... hsa1
* Comment that line by putting a "#" sign in the begining of the line that has hsa1
* Save it.... It won't apear on your desktop when you start ubuntu again.

For fglrx check: [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

---

### Post by aberadam on 2007-05-19
OK, thanks, I'll copy those intructions over to Ubuntu and start playing.  

Thanks a lot.

---

### Post by aberadam on 2007-05-19
OK, I tried manually configuring the settings.  Set the network name and entered the password.  Still nothing.  

Any more ideas?

The 'command line' thing worked but now if I access 'hda1' from places it automatically places a link on my desktop called 'disk' - pretty annoying, I have to 'unomunt' it to get rid of it.

---

### Post by Najand on 2007-05-19
Did you restart your computer?

---

### Post by aberadam on 2007-05-19
Ahh... Will do now.  :)  Woops.

---

### Post by aberadam on 2007-05-19
OK, tried that, didn't work.  Tried manually setting both wireless connections, don't even get the 'BTHomeHub' network coming up at all then. 

So if I select one as roaming I can see the wireless network but can't connect even when I give the correct password in every style possible (WEP 128 bit/ WEP 64 bit/ open user/ shared password).  I get 'Waiting for Network Key' and the icon becomes a blue swirling thing but then it comes up with 'No Connection'. 

If none of the connections are set to roaming I get nothing at all.

---

### Post by aberadam on 2007-05-19
Bump.

---

### Post by u-blunt-2 on 2007-05-20
once youve tried to connect, open up the terminal and type :
```
sudo iwconfig
```
Find the extension which supports wireless functionalities, probably eth1 or wlan. Then, look at the output of :
> sudo iwconfig wlan
or whatever the wireless extension was. look at the KEY value. 
I have noticed that the network manager changes the password. The only options I have are WEP ascii and WEP hexadecimal. 

You can manually enter the password by using this command:```
sudo iwconfig wlan key your_password_here
```
wait a few moments or type 
> sudo iwconfig wlan commit
However, the commit option might not work if you are using restricted modules. 

I would like to know how to get the network manager to use the correct password as running those commands manualy at startup is very frustrating. Hope this helped.

---

### Post by u-blunt-2 on 2007-05-22
Alternatively, look at your /etc/network/interfaces and remove the "s:" before the password key, provided that your key is simple asci.

---

