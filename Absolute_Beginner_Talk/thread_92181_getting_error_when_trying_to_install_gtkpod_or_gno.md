---
title: "getting error when trying to install gtkpod or gnomad2"
date: 2005-11-18
forum: Absolute Beginner Talk
---

### Post by aznboi on 2005-11-18
when i try the GUI apt-get i always get htis message when i try to install those two programs:
```
Depends: libid3tag0 (>= 0.15.1b) but it is not installable
E: Broken packages

```
When i do the apt-get install <packagename> i still get the same message.

what should i do? thnx

---

### Post by tokyovigilante on 2005-11-18
Try       
```
apt-get -f install
dpkg --configure -a
```

and then retry your installation. Are you using the official repositories?

---

### Post by aznboi on 2005-11-19
I tried what you wanted me to do but it didnt work. Then i tried apt-get update but that didnt work either. I still get hte following:
```
The following packages have unmet dependencies:
  gnomad2: Depends: libid3tag0 (>= 0.15.1b) but it is not installable
E: Broken packages

```

any other ideas? thnx in advance

---

### Post by tokyovigilante on 2005-11-20
Try manually. In a terminal:

```
mkdir /home/<your user name>/temp
cd /home/<your user name>/temp
wget -c http://archive.ubuntu.com/ubuntu/pool/main/libi/libid3tag/libid3tag0_0.15.1b-7_i386.deb
sudo dpkg -i libid3tag0_0.15.1b-7_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/universe/g/gtkpod/gtkpod_0.94.0-1_i386.deb
sudo dpkg -i gtkpod_0.94.0-1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/universe/g/gnomad2/gnomad2_2.8.1-1_i386.deb
sudo dpkg -i gnomad2_2.8.1-1_i386.deb
cd ..
rm -r ./temp
```

I'm assuming you're using Breezy i386, if not just modify the above for your architecture (amd64, ppc).

If the above goes well re-run
```
apt-get -f install
dpkg --configure -a
```

BTW, did the two above commands complete without solving the problem or did they fail? If so what errors did you get?

---

