---
title: "Need the sun Java compiler and JRE.."
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2006-12-13
I need to download the sun compiler and runtime environment.. (and whatever else you need to complete the java package for development etc. PLEASE fill me in on what i need)..


I can't have the one that comes with ubuntu.. I need to know these things:
1. How do i get rid of the one I have (to save disk space i suppose? Or should I keep it)

2. How do i download everything i need for development from sun.

3. Please treat me like i know nothing about linux, but i want to learn. So explain what I should do but why i should do it and what its really doing behind the scenes.  And please tell me the easiest way if possible.

Thanks everyone for the help once again.

---

### Post by Delkster on 2006-12-13
> **systemintheglitch said:**
> I can't have the one that comes with ubuntu..

I assume you mean the free/open source Java environment which is installed in Ubuntu by default. You don't really need to get rid of it. It won't conflict with Sun Java if you install the latter one properly.

These instructions apply to Ubuntu 6.10 (Edgy Eft) with the default Gnome desktop. If you use Kubuntu, or an older version of Ubuntu, please let us know.

To install Sun Java:

1. Go to **System > Administration > Software Sources**
2. Enable the checkboxes for community maintained (universe) and legally restricted (multiverse) software. Close the window.
3. Open **System > Administration > Synaptic Package Manager**
4. Search for "**sun-java**" (use the search feature, it's your new friend). You should find packages such as sun-java5-bin and sun-java5-jdk.
5. Select **sun-java5-jdk** for installation. Synaptic will tell you that it needs to install a few other packages as well. Accept that. Also select **sun-java5-plugin** for installation if you want Java applets to work in a web browser.
6. Select "**Apply**" and confirm the changes in the dialog that appears. The Java packages are now downloaded (from the Ubuntu 'repositories', not directly from Sun) and then installed.
7. After the installation has completed, you can close Synaptic.
8. Now you need to tell the system that you want Sun Java to be used as the default Java environment. There are  [ instructions for that in the Ubuntu wiki](https://help.ubuntu.com/community/Java#head-fef9352fb26820bb774df978180c9dd3a60e777b) (enter the commands listed there into the terminal: **Applications > Accessories > Terminal**)
9. Done.

---

### Post by systemintheglitch on 2006-12-13
I have 6.06.

How do i update to the latest version?
Do i need to?

---

### Post by Delkster on 2006-12-13
> **systemintheglitch said:**
> I have 6.06.

How do i update to the latest version?
Do i need to?

No, you don't need to. Sun Java 5 is also available for 6.06. However, my instructions don't apply exactly the same way to 6.06 as they do to 6.10.

I don't have 6.06 installed so I can't write exact instructions, but check out the [wiki](https://help.ubuntu.com/community/Java) for that.

---

