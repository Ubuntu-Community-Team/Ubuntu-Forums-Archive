---
title: "Screen flickers(goes gray and white) at  login"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by fastfinger on 2008-02-28
At the time when I should get a login screen I get a black screen with gray dots like when the cable from tv has been disconnected or something similar (gray dots flickring). I don't remember messing with anything graphics related, the only tihng I did different today was used ntfs-3f to force mount my ntfs partition, but I rebooted 2 time after that and used ubuntu perfectly and this only happene d at the third time. The only other unusual thing I notice is during boot up where it says Loading local boot script from /etc/boot.rc or something similar, goes blank for less tehn a second says that again and so forth 3 times before I get the aformentioned screen. When I do a ctrl + alt+ backspace, it says loading local boot script...... and does nothing else 
although unrelated, i tried booting from live cd and running e2fsck which i did (loads fine on live cd and from xp)

Found the problem atleast, X server ( What I guessed if I may say :s) tred chrooting from a live cd then dpkg-reconfigure xserver-xorg and left everything to default (I just hit enter [neve or something similar was selected by default]) and now, I get a black screen =]. Atleast no flickring gray dots right?
I have used ubuntu for more then 6 months, worked fine on dapper and now on gutsy. Any help appriciated.

---

### Post by fastfinger on 2008-02-28
Okey, I am almost ready to give up, trying to find what the error /something/gdm/defaultXserver too many parameter given on line 47 or somethign similar means, if not, I will just format my partition

---

