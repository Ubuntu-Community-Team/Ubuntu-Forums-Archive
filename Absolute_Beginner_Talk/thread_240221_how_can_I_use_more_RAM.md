---
title: "how can I use more RAM ?"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-08-20
I have 1 GB of RAM
and 2 GB of swap
my CPU isn't that strong - it's P4 with 1800Mhz
some programs/or when I install stuff makes my CPU go to 100%
and using only 25% of my RAM and 1% of swap

I want that more RAM and swap will be used instead of CPU usage
how can I do it ?

---

### Post by Polygon on 2006-08-20
that is not possible, and here is why

the CPU is "the brains" of the computer. All the programs in your computer are run through the processor, which does all the math, tells the other parts of the computer what to do, and other stuff

the RAM is simply a temporary memory for the computer. RAM does not actually do any thinking itself, it just stores information that the programs you are currently running are using so that they can use the information faster then writing to the hard disk

so therefor, the cpu and RAM cannot switch jobs.

---

### Post by jbonll05 on 2006-08-20
Following above posts;
   Is it possible to upgrade your cpu? It is not extremely difficult. What machine are you using, motherboard, socket, and cpu? It would seem you have RAM capacity, and likely the cpu can be updated. If you are not comfortable with doing it yourself check "professionals" in your area for price. Last year(Feb) I paid one in my area $40.00 to learn that I had used a cheap cpu to heatsink grease that cause my machine to overheat. He did provide the good grease. Have not made that mistake again.
JB Ubuntu user since 5 Oct 05 It is the best.

---

### Post by MaximB on 2006-08-20
well...my CPU is pretty old
it's pentium4 1800Mhz - like I've wrote above
it's my backbone , cuz all my other hardware is quite new.
but the CPU costs a LOT , and within a year there should be much better CPU's and cheaper - so I hope to last another year.

---

### Post by kerry_s on 2006-08-20
Man, your specs are better than mine your computer should haul butt. You can speed things up by using alternative app's.
examples:
nautilus=rox-filer
gnome-terminal=xterm
gedit=leafpad

those are the the main things i use everyday, but you get the point use lighter faster apps.

---

### Post by David Corrales on 2006-08-20
I don't think that 1800ghz is extremely old. You should be fine running a lot of stuff since you got enough RAM.
One thing I like about today's technology, is that cpu's advance a lot faster than regular applications do (except maybe games and very cpu intensive stuff :P) so CPU's can be used for several years with good results.

---

### Post by MaximB on 2006-08-20
well - my PC runs fast
but when I installing a program it gose to 100% and almost no uses RAM.

---

### Post by scxtt on 2006-08-20
it should go to 100%, and that's not a problem ... you should be more concerned if it DIDN'T go to 100% ...

---

### Post by Stew2 on 2006-08-20
It's fine for your processor to run at 100%. It wont hurt it or anything. Unless you are having overheating problems or something I wouldn't let it bother you :D .

Regards,
Stew2

---

### Post by MaximB on 2006-08-20
> **Stew2 said:**
> It's fine for your processor to run at 100%. It wont hurt it or anything. Unless you are having overheating problems or something I wouldn't let it bother you :D .

Regards,
Stew2

well...I can bake omelet on it ;)
and I can bake a cake in it.

---

### Post by franute on 2006-08-20
There's a parameter called swappiness that represents how many ram  will the SO use instead of swap. Writting in a shell:
"sudo cat /proc/sys/vm/swappiness"
you should get "60" (it's the default for ubuntu), this says the system should use the 60% of time the swap, so you could reduce it to use the ram more frequently and you get some extra performance. You could reduce it to 10 or 20% (I always use a max of 20%).

How to try it?? Very simple, open a shell and type:
"sudo sysctl -w vm.swappiness=10"
now open some applications and try if you like it now. Then, how to set it to 10 forever? Edit "sudo nano /etc/sysctl.conf" and add in the end of the file "vm.swappiness=10" and it's done. You shouldn't use a very low number if you don't have enough ram or if you are in a server or "compiling" large applications.

You can get more ubuntu improvements in performance here:
[http://www.ubuntu-es.org/node/4440]("http://www.ubuntu-es.org/node/4440")
it's in spanish, so if you need some help tell me, bye! ;)


anyway, your CPU will be at 100% while installing whatever you do

---

### Post by Stew2 on 2006-08-20
> **MAXDDARK said:**
> well...I can bake omelet on it ;)
and I can bake a cake in it.

Mmmm... cake! :D

---

### Post by Damiox on 2008-06-09
> **franute said:**
> There's a parameter called swappiness that represents how many ram  will the SO use instead of swap. Writting in a shell:
"sudo cat /proc/sys/vm/swappiness"
you should get "60" (it's the default for ubuntu), this says the system should use the 60% of time the swap, so you could reduce it to use the ram more frequently and you get some extra performance. You could reduce it to 10 or 20% (I always use a max of 20%).

How to try it?? Very simple, open a shell and type:
"sudo sysctl -w vm.swappiness=10"
now open some applications and try if you like it now. Then, how to set it to 10 forever? Edit "sudo nano /etc/sysctl.conf" and add in the end of the file "vm.swappiness=10" and it's done. You shouldn't use a very low number if you don't have enough ram or if you are in a server or "compiling" large applications.

You can get more ubuntu improvements in performance here:
[http://www.ubuntu-es.org/node/4440]("http://www.ubuntu-es.org/node/4440")
it's in spanish, so if you need some help tell me, bye! ;)


anyway, your CPU will be at 100% while installing whatever you do

  I dont recommend doing that until someone with more rep/experience on the forums approves it....that file is mostly network info....that could open up a security vulnerability....

---

### Post by Koori23 on 2008-06-09
That suggestion is completely valid and has been documented MANY places around here. More detailed direction from ubuntu_demon. I believe a Forum Staff member would have all the reputation you'd need.

[http://ubuntuforums.org/showpost.php?p=1255511&postcount=43](http://ubuntuforums.org/showpost.php?p=1255511&postcount=43)

Besides all that, how is turning off virtual memory (or supressing it, as is this case)CREATING a security threat? I'm awfully curious to know.

---

### Post by Damiox on 2008-06-09
the forum admins are fine...but i dont do jack with out at least 1 second opinion ..that file had a lot of network stuff...and the website is spanish... if i cant read it i dont trust it.....anybody can make a website....

---

### Post by Damiox on 2008-06-09
and ur link is much more thorough ...

---

### Post by Koori23 on 2008-06-09
I totally understand where you're coming from. Don't get me wrong. I was grumpy when I wrote that, sorry.

---

### Post by psyntience on 2008-06-09
Thanks for posting this.  I have 2GB of RAM with an AMD 3800+ and have been noticing very little RAM usage with Hardy Heron.  I'm test driving the vm.swappiness=0 right now and it seems to be running a little faster.

---

