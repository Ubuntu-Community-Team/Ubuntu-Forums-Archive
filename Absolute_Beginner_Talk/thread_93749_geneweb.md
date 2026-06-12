---
title: "geneweb"
date: 2005-11-22
forum: Absolute Beginner Talk
---

### Post by ragwing on 2005-11-22
Hi all;
I installed geneweb from the synaptic package manager and found the documentation for geneweb. It says to run ged2gwb gedcomfilename.ged -o nameforthebase. This ran correct at least according to the documentatioin. 
Now from a browser you type [http://localhost:2317/nameforthebase](http://localhost:2317/nameforthebase).
Here is where I get the error. Cannot access base guinn. The first time I tried it from my home dir, so I figured it could not find the file or there were permission problems. 
Changed these and still had the same problem. So then I copied the .ged file to /var/www/geneweb and re-ran the ged2gwd :confused: Same result. Any help would be appricated. 
Thanks
Rex

---

### Post by Kapre on 2005-11-22
> **ragwing]Hi all said:**
> http://localhost:2317/nameforthebase[/url].
Here is where I get the error. Cannot access base guinn. The first time I tried it from my home dir, so I figured it could not find the file or there were permission problems. 
Changed these and still had the same problem. So then I copied the .ged file to /var/www/geneweb and re-ran the ged2gwd :confused: Same result. Any help would be appricated. 
Thanks
Rex

ragwing - I'm just trying to help (cause I'm not using Geneweb). I just googled and found that there is a forum for Geneweb. It is on [this]("http://sourceforge.net/forum/forum.php?forum_id=387831") site. Maybe you can have more info on it.

K

---

### Post by ragwing on 2005-11-23
Thanks for the reply, I posted this on the site you suggested, we will see if anyone has an answer. I think it really has to do with Ubuntu and the install process. I have installed it before on other distributions from source and it worked just fine. I could do that on Ubuntu also, but it should work out of the box so to speak.
Rex

---

### Post by hengeo on 2006-06-12
> **ragwing]Hi all said:**
> http://localhost:2317/nameforthebase[/url].
Here is where I get the error. Cannot access base guinn. The first time I tried it from my home dir, so I figured it could not find the file or there were permission problems. 
Changed these and still had the same problem. So then I copied the .ged file to /var/www/geneweb and re-ran the ged2gwd :confused: Same result. Any help would be appricated. 
Thanks
Rex

I had problems getting geneweb to work when I first installed it. I then contacted the person responsible for the Genweb software on Linux (Christian Perrier) and he told me that I needed to install also gwsetup for it to work. I have done that, after that I was able to configure it  and finally, I could make it work. Unfortunately, I couls not get it to work with access restriction. When I ask it to use the authorization file, it cannot find it no matter where (directory)  I put it. It just cannot find. The password windows opens up but it does not accept any password.

I hope, you will get as far as I got and someone will suggest a solution to the access problem.

---

### Post by WheelDweller on 2007-08-13
Ah; so I was right: there was no gwsetup included in the package...I wrote him, too, a few days ago and have yet to get a response.

So how did you get gwsetup? Just pull it out of the original distro? (With the matching version name, of course)

---

