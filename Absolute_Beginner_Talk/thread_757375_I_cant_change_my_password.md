---
title: "I cant change my password"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by moehabibi on 2008-04-16
okay .... so my password is " 26841345682" i honestly dont care if you know it .. its not like your gonna come to my house and log in and steall my pictures 

okay soo i want to change it .. or and install XMMS 
but it wont let me type 
when it askes for sudo password ... i try typing 
and it wont let me  
i tried pressing enter then typing the password
but it gives me a error saying thats not the password

how come it wont let me type my passward 

also i tried to do this 

usermod -e moe 2008-04-17 ..

to expire it tomrrow .. 
i tried ALOT random codes 
but im REALLY REALLY new to ubuntu ... like i dont know SHYT ...  and i need help 

BTW 

OFF TOPIC : Music player will not let me play songs from my phillips gogear(mp3 ) 
it says it needs a playback decoder or osmthing like that... can anyone help me .. 
i added the MTP pluig in ... .. and i could see my music .. but i press it .. and it wont play... .. 
and if music play doesnt work ... does XMMS suppport more devices?

---

### Post by tamoneya on 2008-04-16
when you boot you should hit escape when GRUB loads.  Then boot into the recovery mode.  From here type ```
passwd username
```Then put in your new password

---

### Post by Tatty on 2008-04-16
> **moehabibi said:**
> okay .... so my password is " xxxxxxxxxx" i honestly dont care if you know it .. its not like your gonna come to my house and log in and steall my pictures 

No, but someone could get your IP address and then use your password to get into your machine over the internet.  I strongly advise you dont post your password online, and you should probably change it now before someone does try to get in to your machine.

When you are prompted for your password in the terminal it will not show up anything to show that you are typing.  This is a security measure.  Just type the password and press enter.

---

### Post by Dark Aspect on 2008-04-16
> **moehabibi said:**
> okay .... so my password is " 26841345682" i honestly dont care if you know it .. its not like your gonna come to my house and log in and steall my pictures 

okay soo i want to change it .. or and install XMMS 
but it wont let me type 
when it askes for sudo password ... i try typing 
and it wont let me  
i tried pressing enter then typing the password
but it gives me a error saying thats not the password

how come it wont let me type my passward 

also i tried to do this 

usermod -e moe 2008-04-17 ..

to expire it tomrrow .. 
i tried ALOT random codes 
but im REALLY REALLY new to ubuntu ... like i dont know SHYT ...  and i need help 

BTW 

OFF TOPIC : Music player will not let me play songs from my phillips gogear(mp3 ) 
it says it needs a playback decoder or osmthing like that... can anyone help me .. 
i added the MTP pluig in ... .. and i could see my music .. but i press it .. and it wont play... .. 
and if music play doesnt work ... does XMMS suppport more devices?

I think when you use sudo the dialog that ask you for the password does not show the password as you type it.Try entering the password and pressing enter even if it does not show what you have typed.To change you password you can go to system/administration and about me.Then click on "change password".

Also the reason you can't listen to your music is Ubuntu uses ogg files and not mp3s.However you can listen to mp3s if you want but it will require you to install RestrictedFormats.Read this link,it may help:

[https://help.ubuntu.com/community/RestrictedFormats/MP3?highlight=%28mp3%29]("https://help.ubuntu.com/community/RestrictedFormats/MP3?highlight=%28mp3%29")

---

### Post by zvacet on 2008-04-17
```
sudo apt-get install ubuntu-restricted-extras
```

---

