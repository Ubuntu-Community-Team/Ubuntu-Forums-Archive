---
title: "more programs"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by rick21saxo on 2007-05-06
i´ve just installed the barebones minimum version, where can i go to get programs?

---

### Post by junjan on 2007-05-06
Easiest way:

Applications>Add/Remove

---

### Post by rick21saxo on 2007-05-06
where do i go for that?

---

### Post by Marsolin on 2007-05-06
Applications is the menu at the top left of the screen.  Add/Remove Programs is one of the options.

---

### Post by Nekiruhs on 2007-05-06
Click the ubuntu icon at the top right. Select Add/Remove at the bottom.

---

### Post by taurus on 2007-05-06
```
sudo aptitude update
sudo aptitude install program_name
```

Or you can search here, [http://packages.ubuntu.com/](http://packages.ubuntu.com/).

---

### Post by rick21saxo on 2007-05-06
my application tab just has mail agents and WWW browers

---

### Post by Nythain on 2007-05-06
terminal
sudo apt-get update
sudo apt-get install synaptic

search synaptic for any software you want or need, and install either through synaptic, or in terminal with
sudo apt-get program name

---

### Post by junjan on 2007-05-06
[IMG]http://monkeyblog.org/ubuntu/installing/Applications.png[/IMG]

Check this out:

[How to install ANYTHING in Ubuntu!]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by rick21saxo on 2007-05-06
i dont have the full version of ubuntu

---

### Post by Henry Rayker on 2007-05-06
What version are you using, if you don't have the full version? Where did you get it?

---

### Post by junjan on 2007-05-06
Do you have what they called the "Absolute minimum installation"?

---

### Post by taurus on 2007-05-06
Probably a server version, console only.

---

### Post by rick21saxo on 2007-05-06
i have Absolute minimum installation

---

### Post by Henry Rayker on 2007-05-06
Honestly, this installation is more intended for people who have some idea of what they're doing...I would recommend installing a full installation and work from there.

---

### Post by Skrynesaver on 2007-05-06
Hi I'm assuming your machine can't support a desktop/GUI installation and so you are working in the terminal, if so the following gives you a useful way of finding and installing software.  Enjoy :)
```

sudo apt-get install apt-cache
apt-cache search <keyword for program>
apt-cache show <apropriate looking program>
apt-get install <program that does what I want>

```

---

### Post by rick21saxo on 2007-05-06
well the reason why i have Absolute minimum installation, is because my laptop is outdated for the full version and this was the only way i could get ubuntu

---

### Post by junjan on 2007-05-06
If it is a very old machine which can not handle heavy distros, you can try Xubuntu.

They say:

> You can install it by doing a server install of Ubuntu and then fetching and installing the xubuntu-desktop package. The complete process is described at [InstallingXubuntu]("https://help.ubuntu.com/community/InstallingXubuntu")


---

