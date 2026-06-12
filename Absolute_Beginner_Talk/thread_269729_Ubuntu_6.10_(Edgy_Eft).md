---
title: "Ubuntu 6.10 (Edgy Eft)"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by Malice007 on 2006-10-02
When the Final version comes out how would I upgrade to this? Will I just get  a notice like everything else that there is an upgrade and for me to click here to get it? Or do I have to download the whole iso burn it to a cd and reinstall everything?

---

### Post by Bachstelze on 2006-10-02
```

sudo nano /etc/apt/sources.list

```

Change every occurrence of the word 'dapper' to 'edgy', then

```

sudo apt-get update
sudo apt-get dist-upgrade
```

Beware, it will take quite a while, depending n your internet connection speed. If you have a slow connection and want to spare your time, you can upgrade from a CD.

---

### Post by Malice007 on 2006-10-02
being new I should wait till the final version right? Also what is the difference between Edgy and Dapper? Is it just a name that they give it like for example Win98 win2000? Or is this all different all together?

---

### Post by meborc on 2006-10-02
> **Malice007 said:**
> being new I should wait till the final version right? Also what is the difference between Edgy and Dapper? Is it just a name that they give it like for example Win98 win2000? Or is this all different all together?

you should wait until it is final... although there should not be as much complications as there has been, it is still raw material... i would wait until the final is released and a week more so that a lot of people have upgraded and tested it... 

but i must say i use it (read: test it, not on production machine) on my lappy and i have had only minor problems... mostly concerning my internet connection (wifi vs ethernet)

when the final is out, i will reinstall from cd, as i don't want any conflicts between dapper old conf and edgy... it is not nessecary, but i like it clean :)

oh, and to your second Q: edgy is not as radical move as was dapper from breezy... edgy is dapper with lots of new stuff, new kernel, new gnome, etc... no BIG changes, so the upgrade from dapper should be more smooth than it was from breezy to dapper..

hope that helps ;)

---

### Post by Malice007 on 2006-10-02
Yes all of this helped me. Thank you for all the info.

---

### Post by ricardisimo on 2006-10-14
Either installing from cd or via apt-get, I'm assuming that the upgrade will not affect individual files and folders on my comp, correct? I'm a bit paranoid since I lost all of my music and such when I left XP.

---

### Post by PriceChild on 2006-10-14
Check out [http://wiki.ubuntu.com/EdgyUpgrades](http://wiki.ubuntu.com/EdgyUpgrades)

---

### Post by chirayu on 2006-10-14
> **HymnToLife said:**
> ```

sudo nano /etc/apt/sources.list

```

Change every occurrence of the word 'dapper' to 'edgy', then

```

sudo apt-get update
sudo apt-get dist-upgrade
```

Beware, it will take quite a while, depending n your internet connection speed. If you have a slow connection and want to spare your time, you can upgrade from a CD.


Thank you :)

---

### Post by jamesrose on 2006-10-26
> **chirayu said:**
> Thank you :)

when going sudo apt-get update i get this :

```
root@admin-Desktop:/home/admin# sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory
root@admin-Desktop:/home/admin#

```

---

### Post by chuckyp on 2006-10-26
Please use gksu "update-manager -c"    instead of the apt-get dist-ugprade.

---

### Post by Alveric on 2006-10-27
Seconded - can someone make this clear as [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)
doesn't explain.

If I upgrade to Edgy Eft using Update Manager or apt-get, will the uopgrade overwrite all my data files (documents, bookmarks, music etc)??

Can someone who knows more than me please confirm.

Thanks.

---

### Post by viper on 2006-10-27
No, but just in case things go bad i would backup if i were you.

---

### Post by spamzilla on 2006-10-27
> **Alveric said:**
> Seconded - can someone make this clear as [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)
doesn't explain.

If I upgrade to Edgy Eft using Update Manager or apt-get, will the uopgrade overwrite all my data files (documents, bookmarks, music etc)??

Can someone who knows more than me please confirm.

Thanks.

I would like to know this, also is Edgy Eft now "safe" to use. I read some where that it wasn't ready for public use, although I am not sure if that thread was made a few months ago. If someonje could clear this it, it would be great. thanks :)

---

### Post by 505 on 2006-10-27
The installation od Edgy Eft will not delete any of your personal files. If you've made changes to config files, and the installation wants to replace that (with a newer config file) it will ask you what to do (and can optionally show the differences between the files). This makes it very transparent what will the overwritten.
Also, I find Edgy Eft quite stable, however not more or less stable than Dapper. So, it's safe to upgrade to Edgy if you want to now.

---

### Post by Alveric on 2006-10-27
> **505 said:**
> The installation od Edgy Eft will not delete any of your personal files. If you've made changes to config files, and the installation wants to replace that (with a newer config file) it will ask you what to do (and can optionally show the differences between the files). This makes it very transparent what will the overwritten.
Also, I find Edgy Eft quite stable, however not more or less stable than Dapper. So, it's safe to upgrade to Edgy if you want to now.
Thats great, thanks for your replies.

Maybe I'll make that step up to Edgy (have only been on Dapper for a couple of months...)

Another thing: am I right in reading that I can't wait until the end of the Dapper LTS (ie. 3 years) and then upgrade directly to whatever we're on then? That I'd have to do a clean install?

---

### Post by davec64 on 2006-10-27
having a quick scan on the forum and reading the upgrade information, Edgy is  at the final version stage (stable).

Quote from Edgy Upgrades:

*buntu 6.10 is the current stable version of the *buntu operating system. It was released October 26th, 2006. The common name given to this release from the time of its early development was "Edgy Eft".

Hope that clarifies!

---

