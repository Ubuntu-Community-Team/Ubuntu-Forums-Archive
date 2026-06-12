---
title: "Connecting Android 4.3"
date: 2014-09-22
forum: Any Other OS
---

### Post by Banshee-2007 on 2014-09-22
ello everyone


I am almost new to Linuxmint, and I am posting here because Linuxmint is an Ubuntu-based distro, and I found no answer in the Linuxmint forums.

I have got a Samsung Galaxy S3 with Android 4.3 on it. I have tried to connect my phone to the laptop and manage the media and document content, but always ended up with this message ```
 "Failed to open input stream for file" 
```:
[http://imgur.com/t85hMGM,zeVDroe,WLRXUUN,RaYT5Y9,zGC0Rya,tOPiVTh,efGdmUl,huwwJL2#5](http://imgur.com/t85hMGM,zeVDroe,WLRXUUN,RaYT5Y9,zGC0Rya,tOPiVTh,efGdmUl,huwwJL2#5)


I searched in the Internet, and some threads in the Ubuntu forums stated that it is not possible to connect the phone normally to Ubuntu 12.04-based systems with MTP starting from Android 4.0 and greater. I found this explanation below in the link, and applied it:
[http://robert.penz.name/658/howto-access-mtp-devices-via-usb-on-ubuntu-12-04/](http://robert.penz.name/658/howto-access-mtp-devices-via-usb-on-ubuntu-12-04/)


However, the terminal responded with message saying that it is not necessary to do it for the version of Linuxmint (Ubuntu 13.0 and above) I have got :
[http://imgur.com/t85hMGM,zeVDroe,WLRXUUN,RaYT5Y9,zGC0Rya,tOPiVTh,efGdmUl,huwwJL2#6](http://imgur.com/t85hMGM,zeVDroe,WLRXUUN,RaYT5Y9,zGC0Rya,tOPiVTh,efGdmUl,huwwJL2#6)


Nevertheless, I continued, and it took me a while to see the results after I applied the command
```
sudo apt-get upgrade
```


When I rebooted and tried to connect the phone again, the problem arose again and nothing changed. So, Is there any way which I can apply to connect my phone directly to the computer. If there is not, are there any third party software or alternative methods which I can use in this case. Note that I could not connect my phone as "mass storage". Because, I found another thread on the Ubuntu forums which stated that it Android MTP should connect normally with no means to Ubuntu 14.0 and based systems  "http://ubuntuforums.org/showthread.php?t=2231161&highlight=MTP"



Thanks in Advance and sorry for the long thread

---

### Post by howefield on 2014-09-22
And moved to the "Other Operating Systems and Projects" forum.

---

### Post by ajgreeny on 2014-09-22
Have you seen this? It may help.
[http://ubuntuforums.org/showthread.php?t=2226702](http://ubuntuforums.org/showthread.php?t=2226702)

---

### Post by tgalati4 on 2014-09-22
I use ES File Manger on the phone with my GSIII and enable the wireless file sharing.  It works OK.  Not convenient, but it works.  Certainly quicker than waiting for native, plug-and-play support.

---

### Post by westie457 on 2014-09-22
@ajgreeny
The link you posted certainly works for Sony Xperia Z2 phones and tablets. I have been trying to get my phone working via MTP over the last few days.

Thank you for finding and posting the link.

@Banshee-2007
It will not hurt to give the instructions in that link a try.

---

### Post by leclerc65 on 2014-09-22
Did you try Airdroid ?

---

### Post by Banshee-2007 on 2014-11-02
> **ajgreeny said:**
> Have you seen this? It may help.
[http://ubuntuforums.org/showthread.php?t=2226702](http://ubuntuforums.org/showthread.php?t=2226702)


> **westie457 said:**
> @ajgreeny
The link you posted certainly works for Sony Xperia Z2 phones and tablets. I have been trying to get my phone working via MTP over the last few days.

Thank you for finding and posting the link.

@Banshee-2007
It will not hurt to give the instructions in that link a try.


Thanks for your comments guys. I have tried the explanation available in the link you sent, and added a lengthy comment shown in the link below. To sum up what I typed, I tried the method on Samsung Galaxy S2, Galaxy S3, Galaxy S4, Galaxy S4 Active, Galaxy Ace 2, Galaxy Note 3.0 and HTC M8. Galaxy S2 never needed this method to connect normally through MTP, while HTC M8 ran media file (audio/video and images), but required applying the method to run the other files. The other mobile phones including mine (Galaxy S3), never connected through MTP before after applying the changes suggested in the explanation, but my device did connect and allow the management of the **MEDIA (audio, video and images)** content when switched to PTP in the USB connection settings. [COLOR=#000000][FONT=Lucida Grande]Also, the Galaxy Ace 2 connected through Mass Storage USB Connection, as explained in the link below for Android 4.0.[/FONT][/COLOR]
[http://ubuntuforums.org/showthread.php?t=2226702&page=4&p=13158628&posted=1#post13158628](http://ubuntuforums.org/showthread.php?t=2226702&page=4&p=13158628&posted=1#post13158628)

[COLOR=#000000][FONT=Lucida Grande]Mass Storage Connection:[/FONT][/COLOR]
[http://www.device-recovery.com/how-to-connect-android-devices-to-pc-with-usb-mass-storage-mode](http://www.device-recovery.com/how-to-connect-android-devices-to-pc-with-usb-mass-storage-mode)

It turned out that I could at least manage the media content of my phone through the PTP setting.


> **leclerc65 said:**
> Did you try Airdroid ?

Thanks my friend for you comment. I checked about Airdroid. It is nice with the features it provide, but I do not think it is fun to be restricted to 1 GB only with premium subscription !! Especially that I usually transfer files in several GBs of size.


> **tgalati4 said:**
> I use ES File Manger on the phone with my GSIII and enable the wireless file sharing. It works OK. Not convenient, but it works. Certainly quicker than waiting for native, plug-and-play support.

Thanks a lot for your reply mate.
Your idea sounds like a last solution, but not a practical one. At least you can establish a connection when there is no other way to do it. Fortunately, I found that the PTP setting actually works in my phone (Samsung Galaxy S III) and the other phones with the same electronic ID ([COLOR=#FF0000][FONT=Ubuntu Mono]04e8:6860[/FONT][/COLOR]), like Galaxy S4 and Galaxy Note 3.0.

---

### Post by ray^try on 2015-09-18
> **Banshee-2007 said:**
> Thanks my friend for you comment. I checked about Airdroid. It is nice with the features it provide, but I do not think it is fun to be restricted to 1 GB only with premium subscription !! Especially that I usually transfer files in several GBs of size.


You missed something. I never got any "premium subscription" and I able to use Airdroid and copy files infinitely and quick with local wifi. I think you only need the subscription if you got no access for your phone through local network. I encourage you to try Airdroid again because it is the best in this class what I tried (and I tried a lot).

---

### Post by stefanifp on 2016-02-24
You can now try Samsung smart watch to manage your device on Win, Mac and Linux. it's a very convenient tool for device manager.

---

### Post by QIII on 2016-02-24
This thread should have been left to sleep peacefully.

Now it will.

Closed.

---

