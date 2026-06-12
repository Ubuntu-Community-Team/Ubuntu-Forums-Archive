---
title: "permanently Clear_History nautilus history?"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by hopelessone on 2008-02-13
Hi All,

Wanting to permanently clear nautilus history file browser...googled a bit and can only find ways to clear it...but i want to disable it permanently !!

thanks..

---

### Post by chewearn on 2008-02-13
Workaround:

Delete this file:
~/.recently-used-xbel

Create this directory:
~/.recently-used-xbel/



```
rm ~/.recently-used-xbel
mkdir ~/.recently-used-xbel
```

---

### Post by hopelessone on 2008-02-13
no...no...not that one..already did it...(but thanks)

Go to Places >> then Home Folder then in the file browser >> Go >> then Clear_History... << that's the one i want to get rid off....

thanks..

---

### Post by chewearn on 2008-02-13
Ok, understood.  Have a look here:
[http://jazzz1s.blogspot.com/2006/05/nine-things-you-should-know-about.html](http://jazzz1s.blogspot.com/2006/05/nine-things-you-should-know-about.html)

> Nautilus saves a history of the last 10 directories you have visited. When you browse the eleventh directory, the oldest one drops off the list. The history is not saved between sessions and is not written to any file. It lives in the Nautilus process memory and is lost when you logout.

If that is true, I'm not sure if there is a simple way to permanently remove the list.

---

### Post by wiberg on 2008-04-26
While you can't stop nautilus from storing your history somewhere, you can quite easily hide it.

```
sudo cp /usr/share/nautilus/ui/nautilus-navigation-window-ui.xml /usr/share/nautilus/ui/nautilus-navigation-window-ui.xml.bak
sudo gedit /usr/share/nautilus/ui/nautilus-navigation-window-ui.xml
```

There, delete these 4 lines
```
			<separator/>
			<menuitem name="Clear History" action="Clear History"/>
			<separator/>
			<placeholder name="History Placeholder"/>

```

You can mess around with the whole GUI there, have fun!

---

