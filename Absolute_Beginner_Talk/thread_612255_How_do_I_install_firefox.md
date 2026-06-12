---
title: "How do I install firefox??"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by Vektron on 2007-11-13
Hi Everyone!!
 am a newbie to linux ubuntu, always windows, however i like this new os and am wondering how do i install firefox 2.0.0.9 when i already have 2.0.0.6 that came with the cd, there is a lot for me to learn and any and all help will be greatly appreciated.. thanks in advance...
Vektron  :)

---

### Post by zabien1970 on 2007-11-13
Before you do anything read the top sticky

---

### Post by Sef on 2007-11-13
It's updated to 2.0.0.8 now in Gutsy Gibbon, 7.10.    What version of Ubuntu are you using?

---

### Post by rudeboyskunk on 2007-11-13
You'll probably have to remove firefox from within synaptic.  Go to System>Administration>Synaptic Package Manager and search for "firefox."  Click on it and select "Remove Completely."

Then go to [www.mozilla.com/firefox/](www.mozilla.com/firefox/) and install from there (it'll probably have to be a *.tar.gz package, though there might be a *.deb).

---

### Post by philinux on 2007-11-13
Version 2.0.0.9 is mainly a fix for windows so not really worth fretting over.

---

### Post by Billy_McBong on 2007-11-13
[COLOR="Blue"]i think the only difference between 2.0.0.9 and 2.0.0.8(newest version in the repos) is some minor security update
EDIT: philinux beat me to it[/COLOR]

---

### Post by perce on 2007-11-13
> **rudeboyskunk said:**
> You'll probably have to remove firefox from within synaptic.  Go to System>Administration>Synaptic Package Manager and search for "firefox."  Click on it and select "Remove Completely."

Then go to [www.mozilla.com/firefox/](www.mozilla.com/firefox/) and install from there (it'll probably have to be a *.tar.gz package, though there might be a *.deb).

wrong order of operations: how can he go to [www.mozilla.com/firefox/](www.mozilla.com/firefox/) if he has already removed firefox? 

I suggest he first install a second browser (konqueror or opera for example), so that he doesn't get stuck out of the world if he's not able to install firefox from the .tgz.

---

### Post by mcduck on 2007-11-13
> **rudeboyskunk said:**
> You'll probably have to remove firefox from within synaptic.  Go to System>Administration>Synaptic Package Manager and search for "firefox."  Click on it and select "Remove Completely."

Then go to [www.mozilla.com/firefox/](www.mozilla.com/firefox/) and install from there (it'll probably have to be a *.tar.gz package, though there might be a *.deb).

NO. The firefox that came with Ubuntu cannot be removed, as there are many other applications that depend on it. Removing firefox will also remove many other applications with it. And installing Firefox from the package they provide on Firefox website doesn't register it in Ubuntu's package management so those other program's aren't able to use that version..

If really needed, it's possible to install another Firefox version together with the Ubuntu one, but for such a minor upgrade I would recommend just waiting until the updated version becomes available in Ubuntu repositories. It's most likely only going to take a couple of days anyway..

---

### Post by Daveski on 2007-11-13
I strongly advise that unless you have a compelling reason to run a newer version of ANY software in the main repositories, that you stick with what has been 'vetted' to work with Ubuntu. If you stick with what is given (and allow the update manager to give you new versions when they are available), then you will have much less chance of an update breaking something.

---

### Post by llamakc on 2007-11-13
> **perce said:**
> wrong order of operations: how can he go to [www.mozilla.com/firefox/]("http://www.mozilla.com/firefox/") if he has already removed firefox? 

I suggest he first install a second browser (konqueror or opera for example), so that he doesn't get stuck out of the world if he's not able to install firefox from the .tgz.

Open a terminal and use w3m.

```

w3m http://mozilla.com/firefox

```

---

