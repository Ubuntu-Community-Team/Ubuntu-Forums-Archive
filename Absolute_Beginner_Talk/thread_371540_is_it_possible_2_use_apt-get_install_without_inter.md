---
title: "is it possible 2 use apt-get install without internet"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by sarwatj on 2007-02-27
hi everybody 

i have been having a hell of a time trying 2 install softwares on ubuntu dapper
what i did was download the package from the ubuntu official repositry then use the package manager to install those packages and a number of dependencies come up and i needed to download  few more packages.:mad: :confused: 

now i do have an internet connection set up for ubuntu with my connexant modem but i want to use the already downloaded files rather than downloading them all over again (don't have a fast internet connection) how can i change the apt-get to look in my hard disk before checking up on the net

thanks 4 ur help in advance 

regards 
sarwat:

---

### Post by pstep9407 on 2007-02-27
You can use the dpkg command. For help with it, type 

```
man dpkg
```

---

### Post by v8YKxgHe on 2007-02-27
I'm not sure if this will work, but try copying the packages you downloading (as long as they were from the official Ubuntu Packages) to:

> /var/cache/apt/archives/

Then when you use Synaptic/Apt-get it should look at the cache first.

Like I said I don't know if it will work or if you're really suppose to do this.

Edit: Doh, of course. 

```
sudo dpkg -i /path/to/deb/file
```

Or just double click it!.

Ahhh, I hate mornings.

---

### Post by wantime on 2007-02-27
Maybe you could try this link ...

[http://http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories_on_DVDs]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories_on_DVDs")

or in Synaptic -> settings -> repositories

You can have a cd-rom also.  Also this link seems pretty good at first sight:

[http://www.ubuntuforums.org/showthread.php?t=20217]("http://www.ubuntuforums.org/showthread.php?t=20217")

---

