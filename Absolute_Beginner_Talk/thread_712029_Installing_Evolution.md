---
title: "Installing Evolution"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by jswinson on 2008-03-01
I am attempting to install Evolution email client I have tried using both the GUI Adept installer and the command line apt-get with no success. When I use apt-get (sudo apt-get install evolution) I get an error message stating that it is likely that the package is uninstalable it continues to state that there are several unmet dependencies. When I use the GUI installer and select Evolution I get a message There was an error commiting changes. I have tried installing some other packages some have worked and others not, I have a feeling that there is some problem with the installer package.

Thanks

---

### Post by ./. on 2008-03-01
Have you tried *aptitude install* rather than *apt-get install*?

---

### Post by mikeyphi on 2008-03-01
> **jswinson said:**
> I am attempting to install Evolution email client I have tried using both the GUI Adept installer and the command line apt-get with no success. When I use apt-get (sudo apt-get install evolution) I get an error message stating that it is likely that the package is uninstalable it continues to state that there are several unmet dependencies. When I use the GUI installer and select Evolution I get a message There was an error commiting changes. I have tried installing some other packages some have worked and others not, I have a feeling that there is some problem with the installer package.

Thanks

This might seem a stupid question - but how come you are installing Evolution? I ask because it is part of the default OS. 

However, open System/Administration/Synaptic
search for Evolution - when found check to see if it is installed (green square)

Post results!!

---

### Post by jswinson on 2008-03-01
That worked BUT it uninstalled all the Open Office applications is it possible that some versions of Open Office and Evolution can't be run together ?

---

### Post by jswinson on 2008-03-01
In reply to the previous reply about Synaptic this does not seem to have been installed only Adept Manager. I have tried to install Synaptic but I get a BREAK error in red presumably indicating some problem. What I am doing is trying to do evaluate what packages are available so I can find some alternatives to Microsoft OS and Apps. I have had some success installing packages but I don't think that I fully understand the process.

---

### Post by ./. on 2008-03-01
Are you using Kubuntu by any chance?

---

### Post by jswinson on 2008-03-01
Yes I am using Kubuntu

---

### Post by ./. on 2008-03-01
I think Evolution is tightly integrated with the Ubuntu desktop, and I'm not aware of it being available as a stand-alone.

If you *aptitude install ubuntu-desktop* you should be able to get Evolution, along with all of the dependencies required.

---

### Post by dcstar on 2008-03-01
> **./. said:**
> I think Evolution is tightly integrated with the Ubuntu desktop, and I'm not aware of it being available as a stand-alone.

If you *aptitude install ubuntu-desktop* you should be able to get Evolution, along with all of the dependencies required.

Evolution is tightly integrated with the **Gnome** desktop, which is used by the Ubuntu system and not the KDE desktop Kubuntu (which has its own e-mail client, IIRC).

You are correct that a lot of the ubuntu-desktop meta-package contents are required, and installing that is the simplest way to get them all (hopefully there is enough disk space for both window managers.........)

---

### Post by dcstar on 2008-03-01
> **jswinson said:**
> Yes I am using Kubuntu

Please update you forum profile to show this, it saves time knowing what you actually use.

---

