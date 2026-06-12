---
title: "Difficulties with installing Software/ Eclipse"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by rwin on 2006-09-19
Hi,

I'm fairly new to the whole subject of ubuntu. My experiences involve Ubuntu once, with GUI. So basically none...

So, I tried to install Eclipse (so i could use it w/ Java). I chose Add/Remove and chose Eclipse- the packet sources seem to be right as it starting installing. It prompted to insert the cd, so I did. It started and then aborted w/ an error (which i can not recall really).

When I try to (naiv as i am) to install it again, it says it can't, as there are already some files that collide with the installation.

So i searched in synaptic for eclipse files, but didn't find any installed.

What can i do? Is there a way to force a re-install??

i'd glad if someone comes up w/ an idea!

Rajko

---

### Post by Sef on 2006-09-19
Use Synaptic to uninstall it.

System > Administration > Synaptic package manager

Do a search for Eclipse, click on it, and click the uninstall button.

---

### Post by rwin on 2006-09-19
That's the problem, when i do a search for it, it only shows packages that are not installed yet (white square with yellow star). Neither do i see an option that says remove or uninstall. 

what am i doin wrong?

---

### Post by rwin on 2006-09-19
ok, i tried to determine the error, at least it gives you an idea, what happens. what are unmet dependencies? what can i do at this point?

```
root@Laptop:~# apt-get install eclipse
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  eclipse: Depends: eclipse-jdt (= 3.1.2-1ubuntu6) but it is not going to be installed
           Depends: eclipse-pde (= 3.1.2-1ubuntu6) but it is not going to be installed
           Depends: eclipse-source (= 3.1.2-1ubuntu6) but it is not going to be installed
E: Broken packages

```

---

### Post by Brunellus on 2006-09-19
1) do you have the 'universe' and 'multiverse' packages enabled?

[http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories](http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories)

2) if you DO have the universe and multiverse enabled, and you're still having problems, try

```

sudo apt-get -f install

```

which will attempt to fix broken packages.

---

### Post by rwin on 2006-09-19
Hi, i looked for what you suggested, i have all enalbed including multiverse and universe. I'm getting the same error.

i typed:
```

rajko@Laptop:~$ sudo apt-get -f install eclipse
```

any other idea?

rajko

---

### Post by rwin on 2006-09-19
Oh!
Thank god i'm in the beginner's talk. I enabled the sources in the packet manager (this time i actually did it the right way) and it installed eclipse right away. great, it even found the packages automatically, that i had download prior to the error i got while installation.

i had made the mistake of creating another package entry with only universe and one with only mutliverse enabled. does this make trouble?

as so often, the problem sits in front of the computer, but i'm still learning. thank you all!

---

