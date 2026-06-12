---
title: "upgrade to 6.10 from cd"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by orwellus on 2007-04-26
Here I am again:

I would like to upgrade my 6.0.6 Ubuntu to 6.10. I tried to download the upgrade using this command:

gksu "update-manager -c -d"

But kept getting an error message that I had a problem with my internet connection (which is strange since the internet is, and still is, working fine). Anyway. I am going to try to install from the Alternate CD, but my question is how do I install the upgrade without messing up all my data and applications. I would like to do this upgrade since it looks like it has a new version of Open Office, and a faster desktop browser, but I really don't want to spend hours setting up Ubuntu again. Any help would be appreciated.

---

### Post by Seisen on 2007-04-26
You can just change your source list by hand by changing "dapper" to "edgy" or you can copy the source list from here.

[http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_add_extra_repositories")

I upgrade by this way and had no problems with but I don't have anything out of the ordinary installed either.

---

### Post by Josey on 2007-04-26
Be advised that a lot of people ran into problems with the 6.06 - 6.10 upgrade.

It's always better to have /home on a separate partition and format / to start fresh in my opinion.

---

### Post by orwellus on 2007-04-26
Thanks for the replies. Maybe it would be better to build 6.10 on a seperate partition.  I spent most this week and last getting 6.0.6 up and running, and don't want to mess that up. So install 6.10, build it off and on, and then delete 6.0.6 when I get 6.10 up and running. I wish I had just started with 6.10, but Ubuntu sent me the 6.0.6 cd. Oh well. In general, does 6.10 work better than 6.0.6? I like 6.0.6, but it is kinda slow sometimes. I also liked some of the updates featured in 6.10.  Is 6.10 even worth going to all this trouble?

---

### Post by Josey on 2007-04-26
7.04 is the version I would recommend.  It was officially released about a week ago.

---

### Post by orwellus on 2007-04-26
Thanks for the reply. I've heard good and bad things about 7.0.4. Still doing what you recommended, about setting up a new partition,  maybe I can have Ubuntu send me a cd, and give me it try.

---

### Post by Happy_Man on 2007-04-26
First, burn the CD as an .iso and stick in a CD drive. A message should pop up asking if you want to add the CD to the repos. Go ahead and do so. Then, run "update-manager -c -d" and it should let you upgrade!

---

### Post by zvacet on 2007-04-26
If you have Edgy alternate Cd put it in the drive and type in terminal
```
gksu "sh /cdrom/cdromupgrade" 
```

That will upgrade your Daper to Edgy.

---

