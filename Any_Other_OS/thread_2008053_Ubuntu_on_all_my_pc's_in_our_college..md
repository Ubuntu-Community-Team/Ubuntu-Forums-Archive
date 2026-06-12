---
title: "Ubuntu on all my pc's in our college."
date: 2012-06-21
forum: Any Other OS
---

### Post by thomsebastin on 2012-06-21
We in our engineering college are using cent os as server and fedora as client os's..when i asked hod why we were not using Ubuntu,he said "we don't get all packages in Ubuntu by default but in fedora we get almost many of them."..and friend the installation size of fedora s more including all packages by default.
i need to manage our lab from next year but i'm not so familiar with rpm based distros..s there anyway(best way) to instal all these packages by default?or i can even try making a custom .iso by searching all packages i need..but i wonder if there was anything lik the fedora thing.
i need to convince him n install ubuntu there so pls help me out guys.
thanx in advance

---

### Post by zombifier25 on 2012-06-21
You can use uck to make a custom Ubuntu .iso, installing packages into the image using Synaptic.

However, the reasons for using Fedora is rather ridiculous. Does your college have Internet connection?

EDIT: Of course, if you don't have permissions to do so, then I don't think you should replace the computers' OS with Ubuntu. If you college is fine using Fedora, then maybe you don't need to replace 'em. Just read up on how to use a rpm system.

---

### Post by waynefoutz on 2012-06-22
Personally, I'd learn Fedora, although there's no reason you can't dual boot Ubuntu as well. I know at my nephew's University, the engineering department is running Red Hat, you're going to find a lot of that in the workplace as well. It would be to your advantage to become comfortable using Red Hat/CentOS/Fedora as well. Colleges and businesses use it because it's stable andhas a long release cycle.

---

### Post by thomsebastin on 2012-06-22
> **zombifier25 said:**
> You can use uck to make a custom Ubuntu .iso, installing packages into the image using Synaptic.

However, the reasons for using Fedora is rather ridiculous. Does your college have Internet connection?

EDIT: Of course, if you don't have permissions to do so, then I don't think you should replace the computers' OS with Ubuntu. If you college is fine using Fedora, then maybe you don't need to replace 'em. Just read up on how to use a rpm system.

Yes we've internet connection 24*7 .Ubuntu is my favorite,so i wanted it to be used there(except for servers since there r many important files in it.)..he has given me permission to make a custom iso so that we can use it in many pc's..i'll look forward to it.
what s d actual reason as to y Ubuntu is not providing those by default?any issue with patent o anything lik that?i wish there was one such for Ubuntu too.
thanx for d response bro.

---

### Post by thomsebastin on 2012-06-22
> **waynefoutz said:**
> Personally, I'd learn Fedora, although there's no reason you can't dual boot Ubuntu as well. I know at my nephew's University, the engineering department is running Red Hat, you're going to find a lot of that in the workplace as well. It would be to your advantage to become comfortable using Red Hat/CentOS/Fedora as well. Colleges and businesses use it because it's stable andhas a long release cycle.

Oh then i should probably start using fedora/cent ..i think learning it won't be of much difficulty since i'm good with my Ubuntu..(everything has a learning curve at d beginning though..'ll be happy to learn that)..s there anyway now for me to generate a txt file from the fedora to see all the packages that r installed in it?there should be a way right?(like listing all of em using a script o somethin else)

---

### Post by mastablasta on 2012-06-22
> **thomsebastin said:**
> what s d actual reason as to y Ubuntu is not providing those by default?any issue with patent o anything lik that?i wish there was one such for Ubuntu too.

 
you never mentioned what packages you need. you just said packages. as i know fedora has only free packages by default so if you ask me they probabyl have less packages available on install then Ubuntu. 
 
since we don't know what packages would be missing (and that you need) it is hard to give any advice on that.
 
besides if it exists for rhel or fedora it probably exists for Ubuntu as well (either as .deb or PPA). if not there, then there is a source code that can be compiled. 
 
yes you can make a custom copy of ubuntu (remastersys...)

---

### Post by vasa1 on 2012-06-22
> **zombifier25 said:**
> ... If you college is fine using Fedora, then maybe you don't need to replace 'em. Just read up on how to use a rpm system.
Totally +1 that.

---

### Post by Elfy on 2012-06-22
*Thread moved to **Other OS/Distro Talk**.*

I'd make myself an account at fedora forums - or rather you should - I did ;)

You'll find a great deal of information and help there as you do here.

---

### Post by Grenage on 2012-06-22
Fedora is badass, it's well worth getting used to.

---

### Post by Simian Man on 2012-06-22
So you are wanting to replace the operating system on the PCs of an entire department just because you don't have experience with the existing one?  Presumably people use them for actual work and are now somewhat used to Fedora.  Just learn to use it, it's a fantastic operating system and, as others have said, Red Hat and Fedora are frequently used in IT.

---

### Post by Dlambert on 2012-06-22
> **grenage said:**
> fedora is badass, it's well worth getting used to.

+1

---

### Post by Habitual on 2012-06-22
> **thomsebastin said:**
> is there anyway now for me to generate a txt file from the fedora to see all the packages that r installed...

Yes, terminal >
```
sudo rpm -qa > fedora.txt
```

---

### Post by Simian Man on 2012-06-22
> **Habitual said:**
> Yes, terminal >
```
sudo rpm -qa > fedora.txt
```

[LIST=1]
[*]You don't need to be root to run this command.  All you're doing is listing packages.
[*]Fedora does not set up sudo by default.
[/LIST]

---

### Post by thomsebastin on 2012-06-23
Thanx everyone for your answers..i'll get used to fedora..i've dual booted it with my Ubuntu..all my love towards computers came from Ubuntu..so its quiet hard to avoid it..n thanx a ton for the tremendous support..we're also planning to use thin client on some of our pc's..hope everything goes well..i've one month with me to play around in rpm..so obviously i'll make it there.@mastablasta sorry for not providing what packages were needed,actually we installed pretty much every package that came along with d cd..n thanx for d package listing code too.love this community.

---

