---
title: "ubuntu 7.04 same error all the time."
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by mezah on 2007-08-08
hello, i've just installed ubuntu 7.04 its my first linux, i get the same error when i'm trying to update with the "sudo apt-get update" command in the terminal
or when i'm trying to install video drivers from downloaded file, i get this error

E: Malformed 3rd word in the Status line
E: Error occurred while processing nautilus-sendto (UsePackage1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.


any clue?

---

### Post by bwtranch on 2007-08-08
See what you get with " gedit /var/lib/dpkg/status

---

### Post by Hospadar on 2007-08-08
try doing a ```
sudo gedit /var/lib/dpkg/status
```
search for "Package: nautilus-sendto" or just "nautilus-sendto"

you'll be able to sort of see this file is sectioned off by package, so you are looking for the "nautilus-sendto" package.
the second line in the section starts with status, mine looks like: "Status: install ok installed"
It may be that if you just change that line to like what mine says, things will work fine.  if not, try re-installing the "nautilus-sendto" package with ```
sudo apt-get --reinstall install nautilus-sendto
```

I would try reinstalling first, if there really is a problem with the package, it would be better to have it working right as opposed just lying to apt.  If it won't reinstall, then try editing the file and see what happens, if that let's you update, then I would still reinstall the package.

---

### Post by bwtranch on 2007-08-08
#3 I think it's OK to tell a white lie to apt. Because now you can usually use Synaptic to remove the partially installed package. Sometimes it's the only thing that works, (in My humble experience:)

---

### Post by mezah on 2007-08-08
ok when i type "gedit /var/lib/dpkg/status" i get this error :
Could not open the file /var/lib/dpkg/status.

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.


and when i type "sudo apt-get --reinstall install nautilus-sendto" 

i get the first error:

E: Malformed 3rd word in the Status line
E: Error occurred while processing nautilus-sendto (UsePackage1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

---

### Post by SunnyRabbiera on 2007-08-08
I had this issue once, it might be best to alter your sources list and recompile it as there is no easier way I know of fixing it.

did you get any extra repos since you installed ubuntu or did you add more repo's on your own?

---

### Post by mezah on 2007-08-08
> **SunnyRabbiera said:**
> I had this issue once, it might be best to alter your sources list and recompile it as there is no easier way I know of fixing it.

did you get any extra repos since you installed ubuntu or did you add more repo's on your own?

tell u the truth, i i'm not really sure what u mean, it's my first 2 hours in linux enviorment...

---

### Post by mezah on 2007-08-08
any more ideas???

---

### Post by SunnyRabbiera on 2007-08-08
your sources list is a list of where you get your packages from, your sources list might have got messed up by accident even if you didnt add any repo's.

did you try a restart of your computer yet, did you have both apt and synaptic run at the same time?

---

### Post by mezah on 2007-08-08
mmmm....  synaptic wont start i get the same error when i try to open it.
and apt is a command right?? command that i write in the terminal "Advanced Packaging Tool"

thanks for trying...

might be something to do with permissions?, although i think i enabled all of them.

---

### Post by mezah on 2007-08-08
???

---

### Post by Al3xK3aton on 2007-08-08
> **mezah said:**
> ???

Yes indeed, you are a man of many words.

---

### Post by mezah on 2007-08-08
> **Al3xK3aton said:**
> Yes indeed, you are a man of many words.

:tongue:   
i just wanted throw this thread on top again...

but it is going sown so fast :mad:

---

### Post by virilc on 2008-05-13
I copied the /var/lib/dpkg/status and /etc/apt/sources.list files in their respective folders from a known-good working PC and it worked! By the way, I tried this on 8.04 Hardy.;-)

---

