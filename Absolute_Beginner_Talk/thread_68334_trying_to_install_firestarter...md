---
title: "trying to install firestarter.."
date: 2005-09-22
forum: Absolute Beginner Talk
---

### Post by skopas on 2005-09-22
Hello all,
         I dl it to my desktop as an rpm.  I tried to open it and by default it's states archive manager, but dont work.  I opened up terminal and ran sudo apt-get install firestarter and that came up with cant find the file.  Bummer ...i need some assisstance.. :-| 
Any ideas greatly appreciated.   Thanks.

---

### Post by Kapre on 2005-09-22
[QUOTE=skopas]Hello all,
         I dl it to my desktop as an rpm.  I tried to open it and by default it's states archive manager, but dont work.  I opened up terminal and ran sudo apt-get install firestarter and that came up with cant find the file.  Bummer ...i need some assisstance.. :-| 
Any ideas greatly appreciated.   Thanks.[/QUOTE]

skopas - are you using hoary or breezy? If your on hoary, please make sure that the universe/multiverse repo is listed on it. 

K

---

### Post by skopas on 2005-09-22
@kapre,
  Thanks for response.  I far as i know im using breezy.  But, not  100% sure... ](*,) 
I'll check and get back to u.

What is this mulitvers/universe repo thing..????

---

### Post by kingsidy on 2005-09-22
as far as the rpm file, do: "alien <name of package>", then "dpkg -i <firestarter.deb or whatever the thing is called>"

---

### Post by Kapre on 2005-09-22
[QUOTE=skopas]@kapre,
  Thanks for response.  I far as i know im using breezy.  But, not  100% sure... ](*,) 
I'll check and get back to u.

What is this mulitvers/universe repo thing..????[/QUOTE]

skopas - this is the ubuntu backports (where all apps that are not develop/made by Ubuntu resides). I'm using Breezy and just checked on my Synaptic and Firestarter is there. BTW, did you try looking into your Synaptic list, maybe you got Firestarter there already.

K

---

