---
title: "aot-get issues"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by niteblind on 2006-06-13
hi all

i was following the ubuntu guide to install some new programs on my fresh install of dappa and i ran into problems. I wanted to install xmms but when i try i get the following error

E: Couldn't find package xmms

i then tried to install skype and when it tries to connect to gb.ubuntu.com (i think that was the address) it hangs on 0% and keeps on timing out any ideas what i am doing wrong?

cheers in advance

niteblind

---

### Post by taurus on 2006-06-13
Maybe you need to include both universe and multiverse in your /etc/apt/sources.list.  You can edit with gedit and remove the # sign in front of all the lines that have universe & multiverse at the end from a terminal, Applications -> Accessories -> Terminal...
```

sudo gedit /etc/apt/sources.list

```
Save it and then run (from a terminal also)
```

sudo apt-get update
sudo apt-get install xmms

```

---

### Post by niteblind on 2006-06-13
okay i had forgotten the universe etc someon at work had said that too but as soo as i use

sudo apt-get update

it then hangs on 0%, i have an internet connection but it is behind a router is there any portforwarding that needs to be set up to access this service at all?

niteblind

---

### Post by niteblind on 2006-06-14
Hi all

Still getting the problem when i try to run apt-get update where it tries to connect to the server and then hangs. are there more than one of these servers i can connect if so is there a list somewhere? any help would be appreciated

niteblind

---

### Post by underdog on 2006-06-14
Are you getting internet access at all from the machine?

---

### Post by drtvasudevan on 2006-06-14
[QUOTE=niteblind]Hi all

Still getting the problem when i try to run apt-get update where it tries to connect to the server and then hangs. are there more than one of these servers i can connect if so is there a list somewhere? any help would be appreciated

niteblind[/QUOTE]
i had the problem till i removed dhcp and manually entered the DNS settings in network prop
perhaps somethign similar has tobe done.
or a proxy setting for the router is to be done.

regards
tv

---

### Post by niteblind on 2006-06-14
Hi

This is really wierd now. yes i have internet access from the laptop, I statically assign the IPs and DNS on my network (i will try changing the dns servers to my isps in a mo)  I have also set this pc in the DMZ of my router to avoid any port forwarding problems ans still nothing.

i have since tried changing the repository server address to ie.archive.ubuntu.com which i believe comes off of heanet.ie. and the same thing happens.

I tried going into add remove programs as this i read is another front end tothe same thing and this hangs onthe update as well.

any one got any ideas as this is driving me nuts

niteblind

---

### Post by taurus on 2006-06-14
So you can surf the web with firefox but apt-get won't let you connect to the net!

---

### Post by niteblind on 2006-06-14
okay sorted it. it is once again down tothe most useless router in theworld the belkin pre-n router.

somehow it is prohibiting dynamic http transfers i hadnt notced as i specify the proxy i use which !!!!

thanks for the help on this one i am sure i will be back again soon.

---

