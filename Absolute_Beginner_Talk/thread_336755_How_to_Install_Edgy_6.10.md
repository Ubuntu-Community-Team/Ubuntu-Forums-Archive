---
title: "How to Install Edgy 6.10?"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by DanFromWinterpeg on 2007-01-12
Hi again,

I have been considering upgrading to Edgy 6 10 for a while now but I have no idea how anyone has managed to do so since the installer locks up forcing me to do a hard reboot when it scans my HDD partitions at exactly 50% complete over and over again.  I have even burned several different copies of the install CD from different ISO files even, but I have exactly the same result.  I have even reformatted the drives in my PC at least once since the last time I tried.  The installer for Dapper LTS works perfectly everytime.  Does anyone know if the installer for Edgy is different?  It looks the same (I know that with GUIs that means squat ). Can anyone shed some light on this matter.

My second question on the same subject is simply this.  I have Dapper on my system right now.  Is there any way I can just run it as an upgrade through Synaptic Package Manager and bypass the problematic installer completely?

Thanks

Dan

---

### Post by r4ik on 2007-01-12
Replace everything in your sourcis.list fromDapper to Edgy.

sudo gedit /etc/apt/sources.list    and save the file

sudo apt-get update

sudo apt-get upgrade

sudo apt-get dist-upgrade

Should do the trick.

Good luck.

---

### Post by DougieFresh4U on 2007-01-12
Open terminal and do a **sudo apt-get update **then copy and paste this code in terminal and your machine will do the rest::$** gksu "update-manager -c"**

---

### Post by Quillz on 2007-01-12
> **DougieFresh4U said:**
> Open terminal and do a **sudo apt-get update **then copy and paste this code in terminal and your machine will do the rest::$** gksu "update-manager -c"**
This is how I upgraded to 6.10, and other than the fact that it took several hours, I had no issues whatsoever.

---

### Post by r4ik on 2007-01-12
> **DougieFresh4U said:**
> Open terminal and do a **sudo apt-get update **then copy and paste this code in terminal and your machine will do the rest::$** gksu "update-manager -c"**

Did not know about that one ...oh well.

---

### Post by petersjm on 2007-01-12
> **Quillz said:**
> This is how I upgraded to 6.10, and other than the fact that it took several hours, I had no issues whatsoever.

Me too! It took me just under five hours from start to finish, but then I'm not on the fastest of broadbands... When it was do, I had a shiny new Edgy and everything worked perfectly

---

