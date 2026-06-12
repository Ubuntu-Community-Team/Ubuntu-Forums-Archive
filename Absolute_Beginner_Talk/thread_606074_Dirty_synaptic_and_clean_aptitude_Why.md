---
title: "Dirty synaptic and clean aptitude?? Why?"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by offline on 2007-11-07
I downloaded Lincity-ng using synaptic(as an example). There were two or three dependencies besides Lincity&Lincity data. If and when I decide to remove it from synaptic, I understand that some dependencies downloaded with them will remain untouched in my system. Then I should run sudo apt-get autoremove I believe...

OK, one should ask  if this is **logical at all**(why aptitude does a clean job and synaptic does not)? May be this is not the case with 7.10 or will not the case in 8.04?

Thanks.

---

### Post by kyphi on 2007-11-07
In Synaptic, when you want to remove a programme including all its dependencies, choose 'Mark for Complete Removal'.

---

### Post by Maestro23 on 2007-11-07
Good reading:

1.Aptitude:[https://help.ubuntu.com/community/AptitudeSurvivalGuide?highlight=%28Aptitude%29](https://help.ubuntu.com/community/AptitudeSurvivalGuide?highlight=%28Aptitude%29)

2.Apt-Get: [https://help.ubuntu.com/community/AptGetHowto?highlight=%28get%29%7C%28apt%29](https://help.ubuntu.com/community/AptGetHowto?highlight=%28get%29%7C%28apt%29)

3.Synaptic: [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

4.Cleaning the System: [http://ubuntuforums.org/showthread.php?p=800462#post800462](http://ubuntuforums.org/showthread.php?p=800462#post800462)

---

### Post by keyboardashtray on 2007-11-07
If you prefer the GUI method, you could also use the "Status" button in Synaptic.

Installed (auto removable) I believe is what you are looking for, programs that no longer have any dependants relying on them on your system.

Not installed (residual config) has the left over settings, configuration files from programs. This is stuff that would be removed if you marked "mark for complete removal" when you were uninstalling.
Although keep in mind programs leave a hidden directory in your home folder, .programname that has specific user settings.

---

### Post by julian67 on 2007-11-07
> **kyphi said:**
> In Synaptic, when you want to remove a programme including all its dependencies, choose 'Mark for Complete Removal'.

That's not right. Complete removal refers to configuration files, not dependencies.

---

### Post by kyphi on 2007-11-08
Quite right, julian67.

To find the dependencies you can use ```
# apt-cache depends <programme name>
``` before uninstalling the programme.

---

