---
title: "im ready"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by leo5111 on 2006-10-10
i tryed this and im ready 2 tell windows to kiss my *** couple of easy questions first .i have 2 hardrives in windows 1 for windows 1 for storage i plan to set it same way in ubuntu when i install u buntu should i just leave the strage drive unplugged till ubuntu is installed i ask cause if i didnt disconnect 2.nd drive when i did windows it screwed it up they are sata drives  thanx...:p

---

### Post by halitech on 2006-10-10
Linux doesn't handle file systems the same way windows does. maybe check out this podcast for a good info on it

[http://www.linuxreality.com/page/4/]("http://www.linuxreality.com/page/4/")

---

### Post by leo5111 on 2006-10-10
what im sayin though is if i format both but i want to use 1 as the ubuntu drive and the other as storage formattin both will it work?

---

### Post by halitech on 2006-10-10
you would need both of them to be formatted in order to use them but I guess I'm missing exactly what you mean

---

### Post by lemonsCC on 2006-10-10
/ on one and /home on the other? halitech?  I don't know if this is possible and it's late and my/ partition is going bonkers!

---

### Post by leo5111 on 2006-10-10
to play windwows media player videos what codec do i need totem wont play em thanx

---

### Post by oyvindaa on 2006-10-10
> **leo5111 said:**
> to play windwows media player videos what codec do i need totem wont play em thanx

[https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5](https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5)

Try that one.

---

### Post by leo5111 on 2006-10-10
says file already retrieved but when i go to sites that have wmv videos still cant play em?? totem gives some error

---

### Post by Perfect Storm on 2006-10-10
Try with mplayer and mozilla-mplayer then it should work.

---

### Post by leo5111 on 2006-10-10
im a newb can u tell  me how to install 1 or the other? thanx

---

### Post by Perfect Storm on 2006-10-10
First you need to set up this: [http://doc.gwos.org/index.php/DapperGuide#Repositories](http://doc.gwos.org/index.php/DapperGuide#Repositories)
and this: [https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5](https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5)

When done.

```
sudo aptitude install mplayer-386 mozilla-mplayer
```

---

### Post by leo5111 on 2006-10-10
ok i had it set to open with totem i installed everything totem still cant play em playin wmv videos  off sites they arent protected how do i change from totem to what i need to play them?? thanx

---

### Post by Perfect Storm on 2006-10-10
Try uninstall totem:

```
sudo aptitude remove totem totem-gstreamer totem-gstreamer-firefox-plugin libtotem-plparser1
```

You can just install it again if it doesn't work.

---

### Post by leo5111 on 2006-10-10
once i remove totem does it select a new player or do i have to or what?? thanx

---

### Post by Perfect Storm on 2006-10-10
Yes, when you have mplayer mozilla plugin it will use that instread.

---

