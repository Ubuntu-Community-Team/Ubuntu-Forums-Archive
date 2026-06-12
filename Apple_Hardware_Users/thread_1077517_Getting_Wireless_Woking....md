---
title: "Getting Wireless Woking..."
date: 2009-02-22
forum: Apple Hardware Users
---

### Post by WA_Garrett on 2009-02-22
Recently I installed Ubuntu (8.04) on my Macbook. 

Using instructions from this site 
[https://help.ubuntu.com/community/MacBook2-1/Hardy](https://help.ubuntu.com/community/MacBook2-1/Hardy)

I compiled the ath9k drivers for the wireless card. Now my wireless card can detect other wireless networks, but when it trys to connect to them it trys for a real long time, then reports that it can't connect. 

Does anyone know what's going on?

---

### Post by Sysbase1 on 2009-02-22
Close out of everything and try a re-install and see if it work then. It should I'd think.

---

### Post by Romu on 2009-02-23
On Hardy, I think you'd better use madwifi.

---

### Post by WA_Garrett on 2009-02-25
> **Romu said:**
> On Hardy, I think you'd better use madwifi.

I tried both methods for madwifi, I got errors for both of them.

On method 1, when I ran the command
tar -zxvf madwifi-trunk-current.tar.gz
It reported
gzip: stdin: not in gzip format

On method 2, when I ran
cd madwifi
It reported that the directory didn't exist.

---

### Post by WA_Garrett on 2009-02-25
> **Sysbase1 said:**
> Close out of everything and try a re-install and see if it work then. It should I'd think.

I tried that. My computer can detect the wireless networks, it just can't seem to join them.

---

### Post by ghostz on 2009-02-25
have u tried to install Intrepid 8.10 i think it has better wifi managment

---

### Post by Rog-Mahal on 2009-02-25
I believe that the ath9k drivers took a bit more work to get functional. Did you try to install the package from the ppa or compile from source? What kernel version are you using? I think the ath9k drivers needed one of the updated kernels. You could also look at the instructions [here]("http://http://www.thinkwiki.org/wiki/How_to_install_the_development_version_of_atk9k") and see how they compare to the wiki instructions. Be careful, however, because installing conflicting versions can mess things up and it can be messy to clean up.

I did not use ath9k when I had 8.04 running. Instead, I kept madwifi until I upgraded to 8.10. It was just a personal preference, and I know you can get them working without upgrading so it's up to you.

---

### Post by cyberdork33 on 2009-02-25
> **WA_Garrett said:**
> I tried both methods for madwifi, I got errors for both of them.

On method 1, when I ran the command
tar -zxvf madwifi-trunk-current.tar.gz
It reported
gzip: stdin: not in gzip format

On method 2, when I ran
cd madwifi
It reported that the directory didn't exist.
well you have to work with it a bit... these are old instructions that are there just for information as a fallback

The first command's error leads me to believe that the file doesn't exist where you told the command it was... you are going to have to obtain a copy of the madwifi source somehow, and extract it and compile it.

With the second command you listed, the "madwifi" directory doesn't exist. look at where you extracted the code.

---

### Post by WA_Garrett on 2009-02-26
> **Rog-Mahal said:**
> I believe that the ath9k drivers took a bit more work to get functional. Did you try to install the package from the ppa or compile from source? What kernel version are you using? I think the ath9k drivers needed one of the updated kernels. You could also look at the instructions [here]("http://http://www.thinkwiki.org/wiki/How_to_install_the_development_version_of_atk9k") and see how they compare to the wiki instructions. Be careful, however, because installing conflicting versions can mess things up and it can be messy to clean up.

I did not use ath9k when I had 8.04 running. Instead, I kept madwifi until I upgraded to 8.10. It was just a personal preference, and I know you can get them working without upgrading so it's up to you.

I tried to compile it from source. I don't think ath9k is going to work though, how would I clear it off to try and use madwifi?

---

### Post by Rog-Mahal on 2009-02-27
A "quick and dirty" way to prevent ath9k from loading, but not removing the files would go something like this:

```
sudo modprobe -r ath9k
```
then in order to prevent the module from being loaded again automatically you could add "ath9k" to the file /etc/hotplug/blacklist

That's not as good as removing all the files, but I'm a little rusty on that part, and this is all I remember. It's a good tool if you want to compile madwifi and test it in order to compare with the ath9k performance.

---

### Post by tiagobt on 2009-02-27
Were you close to the access point when you tried to connect? In my attempts, the signal strength with ath9k is not very good, so the connection is only stable if you're close enough to the access point. I had the same issue in Hardy and Intrepid. I got better results when I used the MadWifi driver (at least in Hardy). You might be interested in the following thread as well: [http://ubuntuforums.org/showthread.php?t=1080842](http://ubuntuforums.org/showthread.php?t=1080842).

Tiago

---

