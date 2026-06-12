---
title: "Can't Update/Upgrade"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by Trampis on 2008-04-07
I can't seem to upgrade to gutsy from feisty. When I use gksu "update-manager -c" and click upgrade I am given the following message.

> The system was unable to get the prerequisites for the upgrade. The upgrade will abort now and restore the original system state.

Please report this as a bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport. 

also when I attempted
sudo apt-get update
> 
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)

And furthermore when trying to update wine and the system time I am given the following error message.

> W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2007k-0ubuntu0.7.04.1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2007k-0ubuntu0.7.04.1_all.deb)
  404 Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.57~winehq0~ubuntu~7.04-1_i386.deb](http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.57~winehq0~ubuntu~7.04-1_i386.deb)
  

---

### Post by reyhan on 2008-04-07
maybe you have change the repositories to main server in System>Administration>Softare Sorces and download from to main server

---

### Post by mikeyphi on 2008-04-07
Open System/Administration/ Update Manager

Do you have (towards the top) a notice saying "New distribution release 7.10 is available" ?

---

### Post by zvacet on 2008-04-07
System>admin<software sources>third party tab>uncheck all third party repos (medibuntu,wine...).Reload.Use main server instead of your local.

```
sudo apt-get update && sudo apt-get upgrade
```

After this go to the update manager and see if you get message that new version is available for download.

---

### Post by Trampis on 2008-04-09
> **zvacet said:**
> System>admin<software sources>third party tab>uncheck all third party repos (medibuntu,wine...).Reload.Use main server instead of your local.

```
sudo apt-get update && sudo apt-get upgrade
```

After this go to the update manager and see if you get message that new version is available for download.

I attempted this one, and the previous Idea to just use the main server, the problem persists however. 

```
 sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

```

Once I changed to the main server I am told that I cannot get the repositories.

---

### Post by Tatty on 2008-04-09
This error most commonly appears if you have another process running which is using the package management files.  Whenever i see it, it is because I am trying to apt-get in a terminal while i also have synaptic open.

Make sure that you do not have either synaptic, "add/remove programs" or update manager open.  Also check that you do not have another terminal open which may be running an apt-get or aptitude process.

---

