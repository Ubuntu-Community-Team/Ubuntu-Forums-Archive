---
title: "tring to install polymake"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by natman on 2005-11-29
Hi, for the last few days i have been tring without sucess to install a program called polymake ( a maths thing ) as far as i know its not in any repository ( if it is please tell me )

Anyway the web page to go is (click downlaod and installation ,no need to fill in the form and click download,
> [http://www.math.tu-berlin.de/polymake/](http://www.math.tu-berlin.de/polymake/)

My question is which file do i downlaod? I am running  an AMD 64 on Brezzy.

Also after getting the right file, how do i go about installing it? ( an idiots guide please i have never installed in linux before.

Thank You:

---

### Post by teaker1s on 2005-11-29
make sure you have' build-essential' installed or you will get source problems
also worth installing 'checkinstall' as it allows you to easily uninstall unwanted program with synaptic
next
'cd'into the directory
then './configure'
check there is nothing missing in the list it produces (dependencies)
'make'
'sudo checkinstall'

beaware as I found out some source windows only-because of the proceedures it calls
looks like you may need c++ and perl from synaptic

look [here]("https://wiki.ubuntu.com/CompilingEasyHowTo?highlight=%28compiling%29") also

---

### Post by natman on 2005-11-29
Can you tell me exactly which file i need to download?
Also i tried some of the above before and i get an error message telling me that my C is not a n official GNU release? any ideas?

---

### Post by teaker1s on 2005-11-29
when you configure look through the list it creates if you see no or missing then it won't 'make' without trying it I'm not sure-have guests so I must go If you still have problems I'll see what I can suggest, tomorrow

---

### Post by teaker1s on 2005-11-30
have you checked [this]("http://www.math.tu-berlin.de/polymake/")
or you could install 'alien' and use rpm package 
check [here]("http://www.psychocats.net/linux/installingsoftware.php")

---

### Post by steffens on 2007-04-27
hi. if you haven't solved your problem yet. try this:

download the debian package (.deb file) from
[http://wwwopt.mathematik.tu-darmstadt.de/projects/polymake/index.php](http://wwwopt.mathematik.tu-darmstadt.de/projects/polymake/index.php)

then type
sudo dpkg -i (filename).deb
polymake --reconfigure

that's it.

---

### Post by natman on 2007-04-28
Thanks very much for getting back to me, i tired it but unfortunatly my pc is 64bit and the package and i get the following
[HTML]dpkg: error processing ./polymake_2.3-1_powerpc.deb (--install):
 package architecture (powerpc) does not match system (amd64)
Errors were encountered while processing:
 ./polymake_2.3-1_powerpc.deb
[/HTML]

Anyway thanks again for getting back to me.

---

### Post by Bachstelze on 2007-04-28
Obviously, if your system is amd64, a powerpc package won't install. You'll need to grab the source and build it as there is no amd64 package on the aforementioned webpage.

---

