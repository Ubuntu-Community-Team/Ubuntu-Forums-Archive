---
title: "Sun Java"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by IrishGangsta on 2006-07-04
I cannot find the Sun Java package to install it
Is it called sun java or is the filename something other than SUN
Can anyone please help me?

---

### Post by meng on 2006-07-04
To install from repositories, you need multiverse enabled and choose from sun-java5-jre or sun-java5-jdk.

---

### Post by IrishGangsta on 2006-07-04
um i was trying to locate package under the synaptic package manager
I dont know where the repositories are 
and I do not understand how to enable multiverse 
i need some eplaining
if anyone wants to help

---

### Post by meng on 2006-07-04
Yes synaptic is one way of installing from repositories. To add repositories, look here:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by FredB on 2006-07-05
[QUOTE=IrishGangsta]um i was trying to locate package under the synaptic package manager
I dont know where the repositories are 
and I do not understand how to enable multiverse 
i need some eplaining
if anyone wants to help[/QUOTE]

A simple way to enable both universe and multiverse is to use Add/Remove option in Applications menu.

When you're in the add/remove panel, click on both checkbox on the right of the box. And you'll get both repositories activated after clicking on Apply button.

Hope I helped ;)

---

### Post by darkwoofe on 2006-07-05
I have Sun Java installed, but I can't get it to work with Firefox. Can anyone help?

---

### Post by Kilz on 2006-07-05
[QUOTE=darkwoofe]I have Sun Java installed, but I can't get it to work with Firefox. Can anyone help?[/QUOTE]
What version of java did you install and are you running the i386 or amd64 version of Ubuntu?

---

### Post by darkwoofe on 2006-07-05
I'm running the i386 version and I installed Sun Java 5.0 Runtime in order to get better performance out of Azureus (which worked btw).

---

### Post by Rackerz on 2006-07-05
What does Firefox say when you go to a page that needs Java?

---

### Post by darkwoofe on 2006-07-05
There's just blank space where the jave is needed and an icon with the word "Click Here to download Plugin.
When you click on the icon it says Plugins Avalible: Java Runtime Enviroment, then whe you hit next it tries and fails to install the plugin and when you click the Manual Install button it takes you to the Sun Java site.

---

### Post by Rackerz on 2006-07-05
Use this Howto to install Java. [http://ubuntuforums.org/showthread.php?t=76702&highlight=installing+suns+java](http://ubuntuforums.org/showthread.php?t=76702&highlight=installing+suns+java)

---

### Post by LeslieL on 2006-07-05
I've been stumbling around trying to install java, not finding it in Add/Remove Applications anywhere. Then I looked at my /etc/apt/sources.list and saw that all my sources are Canadian (not unreasonably, since I'm in Canada). I added a US source (deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse) and - voila - it's there. I'm now installing it. 

I guess not all repositories are created equal.

---

### Post by darkwoofe on 2006-07-05
I installed via the repository too, but it just won't work with Firefox. I may end up having to remove it and reinstall it myself. 

I do have to uninstall before I follow the instructions in that link, right? And will any of the ones for linux work or do I need a special one?

---

### Post by Sef on 2006-07-06
> I cannot find the Sun Java package to install it
Is it called sun java or is the filename something other than SUN
Can anyone please help me?


IrishGangsta> Are you using Breezy or Dapper?

---

### Post by IrishGangsta on 2006-07-06
I am using Dapper i believe it's the new version 6.06

Thanx to FredB i installed sun java 5 and that works

Then i was looking for java runtime environment and i foound it

It's not called java runtime its called Java Web Start which was also located in add/remove programs - Blackdown Web Java start

Thank you Fred B ....You the Man!

---

### Post by IrishGangsta on 2006-07-06
Alrite i need to add now
The websites are still running correctly
But at the top it still says i am missing the java runtime environment plug in

Even tho the site runs okay.

If anyone could help me out with this situation

---

### Post by darkwoofe on 2006-07-06
Same problem I'm having.

---

### Post by Nikusan on 2006-07-06
[QUOTE=darkwoofe]Same problem I'm having.[/QUOTE]

You both need to install this package: sun-java5-plugin

---

### Post by darkwoofe on 2006-07-06
[QUOTE=Nikusan]You both need to install this package: sun-java5-plugin[/QUOTE]

Worked like a charm Nikusan! Thank you.

---

