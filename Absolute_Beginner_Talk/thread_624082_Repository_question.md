---
title: "Repository question"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by Casual Fan on 2007-11-26
I did a quick search and couldn't find this anywhere--sorry if it's been answered before.

Question: When do restricted drivers make it into the official Ubuntu respository? For example, I'm using an older version of the ATI restricted driver (fglrx) that I downloaded automatically when Ubuntu told me it was available, right after my install. It works fine, but there have been maybe 4 versions since this one--and the newest is rumored to not cause suspend to fail. And I'm not crazy about installing anything through the command line. It seems like every solution that involves the command line creates 10 more problems...

Does Ubuntu freeze the repositories with the drivers available at the time when the latest Ubuntu release comes out, or are things added along the way if they're shown to be "stable?"

Thanks

CF

---

### Post by Casual Fan on 2007-11-27
Nothing?

---

### Post by FuturePilot on 2007-11-27
The repos are frozen at release, so whatever version was the latest at the time will be the one in the repos. They don't get updated once the repos are frozen.
Though if you wanted the latest driver you could use [Envy]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by melenor on 2007-11-27
so that means that the only ATI Driver available though ubuntu without using the terminal is the 8.37 versoin and it will never be updated to 8.42 because the repos are frozen, why can't they just update the repos, it shouldn't be that hard should it?
btw i have tried many a time to install the latest ATI driver though terminal many a time and i have always had a problem come up.

---

### Post by mcduck on 2007-11-27
> **melenor said:**
> so that means that the only ATI Driver available though ubuntu without using the terminal is the 8.37 versoin and it will never be updated to 8.42 because the repos are frozen, why can't they just update the repos, it shouldn't be that hard should it?
btw i have tried many a time to install the latest ATI driver though terminal many a time and i have always had a problem come up.

Updating a single package is not hard, but keeping all tens of thousands of packages updated while also making sure that no update causes any problems or conflicts with other stuff is pretty much impossible if the operating system is supposed to be stable and usable in servers and corporate environments as well.

Therefore Ubuntu uses 6 month release cycle and only provides security updates and fixes for serious bugs between the version releases.

---

### Post by Casual Fan on 2007-11-27
Thanks for the info! :)

---

### Post by melenor on 2007-11-27
but isn't the ATI Driver a single package? can't they update that, and shouldn't the update of the ATI Drivers only help any problems for ubuntu

---

### Post by nhandler on 2007-11-27
It may only be 1 package, but consider this situattion...
Package X uses the ATI uses a file called myfile that is provided by the ATI package. In the newer version of ATI, myfile is replaced by superfile. This would break Package X.
So you see, by updating one package, it could cause one or many other packages to break. That is why they freeze the repos, to keep them stable.

---

### Post by melenor on 2007-11-28
Does that mean that the ATI driver will never be updated for 7.10 and i will need to wait until 8.04 to get 8.42 or are they going to relaese an update before that will update the drivers, because i seem to remember that with 7.04 that i downloaded an update to the ATI driver?

---

### Post by FuturePilot on 2007-11-28
> **melenor said:**
> but isn't the ATI Driver a single package? can't they update that, and shouldn't the update of the ATI Drivers only help any problems for ubuntu
It's too low in the system for that.
> **melenor said:**
> Does that mean that the ATI driver will never be updated for 7.10 and i will need to wait until 8.04 to get 8.42 or are they going to relaese an update before that will update the drivers, because i seem to remember that with 7.04 that i downloaded an update to the ATI driver?
Yes.

---

### Post by melenor on 2007-11-28
how long would it take for them to do the neccessary things to allow them to relaease an update that would allow use of the ATI 8.42 Drivers because the new drivers are supposed to be a big improvement over the 8.3 drivers

---

### Post by FuturePilot on 2007-11-28
Gutsy will never get the 8.42 driver. You'll have to either just wait for Hardy, or install them manually or use Envy.

---

### Post by mcduck on 2007-11-28
> **melenor said:**
> but isn't the ATI Driver a single package? can't they update that, and shouldn't the update of the ATI Drivers only help any problems for ubuntu

Yes it is, but so are many other programs. There are at least hundreds of single-package programs that have newer versions available than what are in repositories currently.. It makes no difference, one program depends on others and they depend on many others again.

Like I said, Ubuntu releases only get security updates and fixes for serious bugs. New driver version is neither one.

If you want later versions of software than what are available in repositories you have to install them yourself, and on your own responsibility.

(just before anybody says anything, installing latest versions of programs and drivers _is_ possible and easy in Windows. The difference is that you always do it on your own responsibility, Microsoft doesn't care if you break your system, and they don't even try to make sure that most popular drivers and software work correctly. It's your problem, not theirs. Ubuntu works differently and it's developers do their best to give you a stable package, including the OS, drivers _and_ applications..)

---

