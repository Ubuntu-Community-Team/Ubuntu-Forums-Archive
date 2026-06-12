---
title: "Stupid Apt-Get Update Question"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by FoggyMtn on 2006-08-08
Hey ya'll

I'm running Dapper Ubuntu on my desktop.  I try to only use the gui when the command line fails me (I'm trying to learn linux. ;) ).  WHen I see the red icon in the upper right corner telling me I have X number of updates available, I type sudo apt-get update in the CLI.  THe repositories are contacted and the cycle completees.  The red icon goes gray and says a package manager is working.  But then it resets to red and says I have the same X number of updates.

WHere am I going wrong?  As I read the helps and wiki, I must be missing something, because this is supposed to be easy to do! LOL

THanks for the help
rob

---

### Post by Jagot on 2006-08-08
You need to upgrade as well:

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by xpod on 2006-08-08
when i do that i use
```
sudo apt-get update
```

Then
```
sudo apt-get upgrade
```

Not sure if that helps

BEAT ME TO IT...haha

---

### Post by FoggyMtn on 2006-08-08
So by just seeing the red icon, there is no way to tell whether an update will fix it, or if it will require an upgrade.  Right?  Is there any reason NOT to just run both on a regular basis?  Or are some updates/upgrades not always the best thing to install?

Thanks for the quick reply
rob

---

### Post by Jagot on 2006-08-08
Update just updates the cache of available stored on your computer - it does not download the packages.  If you want to download those extra packages that its telling you you need to download then you have to do both update and upgrade.

It is always advisable to download updates - a lot of them are security related updates.

---

### Post by gruffy-06 on 2006-08-08
Not really. The icon only tells you that updates are available and you can get them. It automatically runs apt-get update in the background by default and notifies you.

---

### Post by Kaloma on 2006-08-08
They are two different operations: **update** simply refreshes the packages list from the repositories, whereas **upgrade** installs the latest available versions of your packages.  You must update to know what the latest versions are, and then upgrade to actually install them.

Matthew

---

### Post by FoggyMtn on 2006-08-08
Thanks for explaining it and taking the time

Have a great week!

Rob

---

### Post by xpod on 2006-08-08
So as i asked somewhere else should apt-get never be used as apse to the aptitude one instead
Never noticed that...

---

### Post by Jagot on 2006-08-08
> **xpod said:**
> So as i asked somewhere else should apt-get never be used as apse to the aptitude one instead
Never noticed that...

[http://psychocats.net/ubuntu/aptitude.php](http://psychocats.net/ubuntu/aptitude.php)

---

### Post by The Seeker on 2006-08-08
I understand your wanting to use the CLI wherever you can to learn your way around but I'd suggest you just let the update manager do its job.

I use the CLI quite a bit to search for packages, man pages etc but I figure why make things harder than they need to be? After all, your computer should serve you, not the other way around.

---

### Post by xpod on 2006-08-08
Thanks for that.....ive only been using this for a week so nows as good a time as any to realise the pro`s n cons of the 2...cheers

---

### Post by mscman on 2006-08-08
> **The Seeker said:**
> I understand your wanting to use the CLI wherever you can to learn your way around but I'd suggest you just let the update manager do its job.

I use the CLI quite a bit to search for packages, man pages etc but I figure why make things harder than they need to be? After all, your computer should serve you, not the other way around.

Actually, I always use the CLI to upgrade my packages, since I prefer aptitude to apt-get. It handles dependency errors much better during upgrades, and I can choose which way I want errors to be handled. A great example of this is Compiz/XGL and the theming situation that's been happening with CGWD. They dropped gcompizthemer as a dependency and actually made it a conflict with the new CGWD package, since CGWD now includes the themer. The default action to be taken was to ignore the CGWD upgrade, but I was able to skip that option and choose instead to uninstall gcompizthemer.

Long story short, I simply create and alias so I can type "upgrade" in the terminal and it will do an aptitude update && aptitude upgrade.

---

