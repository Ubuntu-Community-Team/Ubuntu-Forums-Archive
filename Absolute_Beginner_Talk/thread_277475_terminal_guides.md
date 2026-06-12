---
title: "terminal guides"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by eldar on 2006-10-14
OK well I got ubuntu installed and updated. I have managed to install flashplayer and adobe reader, however I have been trying to install mplayer and was able to get some of the dependancies installed but there are others needed. Short of trying find all those, I tried to get a package and install that but cant. Part of the problem is my lack of knowledge of terminal and the commands needed to install things and just basic operations. Big change from windows as you all know. I like XP but have been less than impressed with vista. Want to get started on linux cause you just never know. 

Anyone have some guides they could throw my way that are well-explained?

---

### Post by aidanr on 2006-10-14
lots here ;) 
[http://www.ubuntuforums.org/forumdisplay.php?f=100](http://www.ubuntuforums.org/forumdisplay.php?f=100)

i'd suggest installing mplayer with automatix

---

### Post by eldar on 2006-10-14
Tried that and could not get the commands to work in terminal to get automatix.:-k

---

### Post by aidanr on 2006-10-14
post the output of the commands

---

### Post by eldar on 2006-10-14
ok it is a  bit long but I get towards the bottom and it asks for my password and I put it in and then nothing. Probably something simple but with my near-zero ability right now.....

eldar@eldar-laptop:~$ automatix2
bash: automatix2: command not found
eldar@eldar-laptop:~$ wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
--16:39:40--  [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
           => `key.gpg.asc.3'
Resolving [www.getautomatix.com](www.getautomatix.com)... 82.165.194.143
Connecting to www.getautomatix.com|82.165.194.143|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,730 (1.7K) [text/plain]

100%[====================================>] 1,730         --.--K/s

16:39:40 (35.87 MB/s) - `key.gpg.asc.3' saved [1730/1730]

eldar@eldar-laptop:~$ gpg --import key.gpg.asc
gpg: key 521A9C7C: "Justin Hayes (Automatix Repository Master) <wildtangent@w1ldt4ng3nt.net>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
eldar@eldar-laptop:~$ gpg --export --armor 521A9C7C
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1.4.2.2 (GNU/Linux)

mQGiBESDLOwRBAC0UwJJgmJ0GWL0DZvTrZq/754uEg1Adx/37Sa6pRYku3JzH69C
+X4lm/JFdBdGfCgjYit8w7Qvg7BNOsgeT6HrjWzHA0Zby5iwb+qSVrOD6zoBoe2z
/Iw6jcZH8Ik90irnD/xbpFqp3E+hZHLreKnM+B6TNiXfknw5HIHNhLG5YwCgv/sL
GxZJEfH7JkiOZHGnxUstzpED/jLfA15ZLUgqGLQBoD7Qb3RDgiMW/KSK4aXet73y
LlYA3g7K7AeRfPNIncg098jRZ3PlWTarRX6mVRiuWRsZi8FSKwMDnURouYpoNhjs
BiFxoUOtuxg5wpdYgh9MqyzMWPIu17Rr7h06jekRJYrZl84yOgwd8E6FzTSkVy1p
SYfLA/0XorCH/JMtecFzcUQJ7+TKI5Fr+kbls6/qXcEVDCbWGj17WZve00XfB6AA
v3L4+5bNYhoV7k+BBN1oX3rZz84yo9cHoaks3UpuIkE4qiGDvRvk9ALebmVrTmd2
dCydVNk3iu1tRKDytYM3YZjTzxwUdl6Qst4fe4CzTQ+NoPzE+bRISnVzdGluIEhh
eWVzIChBdXRvbWF0aXggUmVwb3NpdG9yeSBNYXN0ZXIpIDx3aWxkdGFuZ2VudEB3
MWxkdDRuZzNudC5uZXQ+iF4EExECAB4FAkSDLOwCGwMGCwkIBwMCAxUCAwMWAgEC
HgECF4AACgkQGLUv41IanHyI+QCdFN8YUHU2+RwikJhBHiaCV0YDMfQAniEuUS2u
cGnT//nvDqmcnLmqepI5uQINBESDLPoQCAD6+GPDOWl4u/o+KNBXcmWVaFCq8yiq
M2v5FMx54rZ4otx3DJBsZslEMNrErT4N5q3MmmL9hb6EXlh0ciEAiNyTckNcgH2Q
fiFC5P8eaAfQD/dLRvRcAJyXmW6Hwkhx4JLfxP7SjQs+sxVy4i2MDHlqCCwrIX1S
fU4fXSdobq6BYbapJv7zCK5hFMqwKaXLnYbpCFqNasbZ2XJXii5y7/RTNVOHGNgv
nQMOy0PlKahj2lpwjjdCGbWVsiH+kj/+jc2eEr4qlyUp7j7f0j0Hpv+bzpDDz4gt
qrQTq2lgFIojJ/kEasO9IIG3/Lm10+cWITV5Pgkfvp6u045IbEhDUg6DAAMFB/91
MXdQHUDQesKFPPUAyI42/gun9zkYSoCgD1Iji8YfaY++tQufpAF26SyDhb3Oiesn
nB2/2aFloVMGxKbmiWtzm780WoOuxVzG9wTnaky2V0r3U2+pRhm+if/o4y0lk4cH
9Q7Kg5TZZ6i2MS4FG4mgFgF9uza4m4GmixYWWe4aX+xyBKhoKYtgfKiAoSS7Rl0w
tM5c7VXOgi9VdpMxpsg+pWwQlu+L5YssEEgOCz24RsUqcqjKVEQevRDuHd65IvS6
llfhTT2oYyoIR4cELgo8/Uup0nKMd1t1oyzpGxebNiUE2nKw1luGIl+p5jq8LEym
x500HlKQAwCyBr37y8QniEkEGBECAAkFAkSDLPoCGwwACgkQGLUv41IanHyfugCg
pRNJJUwzOG4JsEYgadhNBQ4dBesAnjW5AW6pG9z/0vk0IaLLVj4An5J1
=Vq+Z
-----END PGP PUBLIC KEY BLOCK-----
eldar@eldar-laptop:~$ sudo apt-key add -
Password:

---

### Post by r4ik on 2006-10-14
> **eldar said:**
> Tried that and could not get the commands to work in terminal to get automatix.:-k

For Automatix try this link please,

[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_Automatix2_on_.28K.2FX.29Ubuntu_6.06_i386.2C_AMD64_.28Dapper.29](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_Automatix2_on_.28K.2FX.29Ubuntu_6.06_i386.2C_AMD64_.28Dapper.29)

Here's another link that might be of use just read,copy and paste :)

[http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Player_.28Mplayer.29_with_plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Player_.28Mplayer.29_with_plug-in_for_Mozilla_Firefox)

Original link,

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

Good luck !

---

### Post by aidanr on 2006-10-14
did you add the repository
```
sudo gedit /etc/apt/sources.list
```
and add to the bottom
```
deb http://www.getautomatix.com/apt dapper main
```

also you have to run these commands
```
sudo apt-get update
sudo apt-get install automatix2
```

---

### Post by eldar on 2006-10-14
That first link is the one I have been trying to follow.

---

### Post by eldar on 2006-10-14
well I may not have done the repository but the sources list I did there was a second one but is supposedly for K/X ubuntu so I did not do those.

the second item I did not put in so will have to try that one. The last 2, my terminal stops after that password those no matter what I type, they do nothing.

wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -
 I make it to this part and THIS line between 521A9C7C and sudo, is there a key for that or is that something else?

---

### Post by r4ik on 2006-10-14
No need to do the post install bit just,

Edit your sources.list:

sudo gedit /etc/apt/sources.list 

from terminal

Substitute gedit with the text editor of your choice.

Add the following to your sources.list:

NOTE: Kubuntu/Xubuntu users will need to uncomment all the additional sources as well as add the automatix repository.

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

Now save the file and close it.

Next you must get our GPG key in order to authenticate our repository from terminal:

wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -

To finish off:

sudo apt-get update
sudo apt-get install automatix2

Good luck !

---

### Post by eldar on 2006-10-15
Well I went thru and removed my list change, saved, then dedid it. was able to copy paste the terminal commands and now have automatix. Sure made installing mplayer easy!

I still do not know how to type in that verticle line in one of the commands!

Thanks guys. Now to read up on the terminal guide. I may actually learn something....maybe8)

---

### Post by ReaderRat on 2006-10-15
> **aidanr said:**
> did you add the repository
```
sudo gedit /etc/apt/sources.list
```
and add to the bottom
```
deb http://www.getautomatix.com/apt dapper main
```

also you have to run these commands
```
sudo apt-get update
sudo apt-get install automatix2
```
Do the above and it works every time for me. Learning how to do it is worth the time & effort, because this gives you an easy way to install most of the stuff you will need in Ubuntu. Spend a few minutes doing this and save hours later.

EDIT Sorry, I'm too late. Enjoy Automatix.

---

### Post by r4ik on 2006-10-16
> **eldar said:**
> Well I went thru and removed my list change, saved, then dedid it. was able to copy paste the terminal commands and now have automatix. Sure made installing mplayer easy!

I still do not know how to type in that verticle line in one of the commands!

Thanks guys. Now to read up on the terminal guide. I may actually learn something....maybe8)

Little late sorry,

|  is shift  \ button
on my keyboard that is.

---

