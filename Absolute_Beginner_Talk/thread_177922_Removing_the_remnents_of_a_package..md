---
title: "Removing the remnents of a package."
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by ProjectGod on 2006-05-17
hi gang,

its a simple thing to remove applications and services on a windows machine. all you need to do is unstall it and clean out the residue from the registry.

how might you accomplish this on ubuntu linux?

is "apt-get remove xyz" enough? or do i need to do more?

i find after installing and removing a few packages the system has become a tad bit slower than it used to be. it hasn't stalled on me just yet after about 2 weeks of use... but it sometimes appears to have stalled. it locks up for about 30 seconds with no interaction then it starts to work again.

cheers.

---

### Post by Jimmey on 2006-05-17
> sudo apt-get --purge remove xyz

Will remove the package, and it's configuration files. If you don't use the --purge option, the configuration files will be kept, incase you want to re-install.

You might also want to try 
> sudo apt-get clean to clean all the downloaded packages from the apt cache.

---

### Post by mcduck on 2006-05-17
You can also install deborphan, and then make new filter in Synaptic to show only orphaned packages. (packages that have been installed as dependencies for some app, and that are left on the machine after removing the original app)

---

### Post by ProjectGod on 2006-05-17
cheers :)

by the way would removing the directory be a good idea? lets say /etc/samba

i tried to "sudo apt-get --purge remove samba" but smb.conf and other files were still there under /etc/samba... i don't think they were there to begin with(??)

---

### Post by mcduck on 2006-05-18
[QUOTE=ProjectGod]cheers :)

by the way would removing the directory be a good idea? lets say /etc/samba

i tried to "sudo apt-get --purge remove samba" but smb.conf and other files were still there under /etc/samba... i don't think they were there to begin with(??)[/QUOTE]
I just checked, and the /etc/samba directory are there by default, probably because default install includes samba client (but not server).. So you'd better leave it there.

---

### Post by ProjectGod on 2006-05-18
good thing you told me. i was going to remove everything under that directory ... and the directory itself!

---

### Post by ProjectGod on 2006-05-19
more package queries... i didnt want to make a new thread so i'll dig up my own. 

ahem... when i type "apt-cache show xyz" it shows the package and the "dependencies"... take for example "netmrg" package... one of the dependencies for this app is "apache". 

a question... do the "dependencies" automatically get installed as well? it kinda asked for my ubuntu 5.10 breezy cd when i typed "sudo apt-get install netmrg"

i decided to get netmrg. so after getting it it got a little complicated with mysql databases etc etc.. i removed it. however after removing it i noticed apache and php4 and a whole hoard of other "services" remaining on my ubuntu machine. were they there to begin with?

i just don't like the idea of package residue being left behind on my system :evil:

----------------

one more question... how can you check the services currently running on the system? is "top" the only way?

you should know i suffer from a obsessive / compulsive disorder 

cheers.

---

### Post by mcduck on 2006-05-19
When you install something with apt-get, all dependencies will also get installed. (and that's good, as the app you install really needs those packages, that's why they are called dependencies ;)). Removing a package won't remove it's dependencies though. But that's often a good thing, for example you can remove the ubuntu-desktop package without loosing Gnome, Firefox and all other apps that come with the default install.

But if you install something with aptitude instead of apt-get (sudo aptitude install packagename) removing the package (sudo aptitude remove packagename) will also remove all dependencies if no other package needs them. (if you installed the package with apt-get, removing it with aptitude doesn't work) So when you install something you're not sure you'll keep, use aptitude instead of apt-get :)

---

### Post by eentonig on 2006-05-19
mcduck, I installed deborphan and created a filter 'residual config' + 'Orphaned'.

Is it safe to select the output and mark them for complete removal? It should be, from how I see it. But just checking to make sure.

---

### Post by mcduck on 2006-05-19
[QUOTE=eentonig]mcduck, I installed deborphan and created a filter 'residual config' + 'Orphaned'.

Is it safe to select the output and mark them for complete removal? It should be, from how I see it. But just checking to make sure.[/QUOTE]
Yes, it's safe.

If it wasn't, I wouldn't have even mentioned deborphan here. ;)

---

### Post by ProjectGod on 2006-05-19
COOL. 

aptitude. i've never heard of that one... i'll give it a whirl. thanks for the reply mcduck :D

---

### Post by ctgray on 2006-05-20
I'm suprised more people don't use it.

---

### Post by eentonig on 2006-05-20
Ok thanks. I'll clean up some space on my HD then. 
Hope I don't have to come back to prove you wrong :mrgreen:

---

### Post by saphil on 2006-07-28
Thanks for the tip
I used apt-get clean and got rid of the 4660 packages in the /var/cache/apt/archives from 3 upgrades.  Cleared almost 3gb of space (98% of the /var partition was ful)

---

