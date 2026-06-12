---
title: "nautilus file search?"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by Ansible on 2007-07-15
It seems that you can't use nautilus to search from location 'file system'.  I can choose a sub folder through, like 'lib', and search there.  its pretty tedious though, if I'm looking for a file and I don't know what subfolder its in.  Is this really the way this is supposed to work?

---

### Post by p_quarles on 2007-07-15
Some people don't like it, but I've found that the Beagle search tool works very well for my purposes. Search the repos for beagle.

---

### Post by mikewhatever on 2007-07-15
I had a similar experience with nautilus search function. It took a long time and usually found nothing. The simply solution I've found was to use the terminal search command
> locate file_name
There are no fancy graphics, but the search is very fast. You can also use parts of names, if don't remember the exact ones.
If you must have a graphic tool, Beagle should do, or Google Desktop for Linux.

---

### Post by Ralob on 2007-07-15
> **p_quarles said:**
> Some people don't like it, but I've found that the Beagle search tool works very well for my purposes. Search the repos for beagle.

hey, thanks for that rec. I am going to try this tonight :)

---

### Post by Ansible on 2007-07-15
Thanks for the tips.  It seems a shame that something so basic fails the grandma test.  For it to just not work for no apparent reason is not intuitive.

---

### Post by nhandler on 2007-07-15
> **mikewhatever said:**
> I had a similar experience with nautilus search function. It took a long time and usually found nothing. The simply solution I've found was to use the terminal search command

There are no fancy graphics, but the search is very fast. You can also use parts of names, if don't remember the exact ones.
If you must have a graphic tool, Beagle should do, or Google Desktop for Linux.

If you do use the locate command, be sure to run 'sudo updatedb' before you do. The updatedb command updates the database that locate searches. That way, you ensure that it finds every file.

I've tried google desktop, beagle, and nautilus search. Out of those, I like google desktop the most. It takes a while to index your computer initially, but after that, it is great.

My overall favorite would have to be locate. Since it is terminal based, I can pipe it to other commands such as grep and sort.

---

### Post by sancho panza on 2007-07-15
I too have run into this problem with Nautilus search; not being able to search subfolders. Struck me as rather odd. [Tracker]("https://help.ubuntu.com/community/MetaTracker") seems like a way around, havent been able to use it yet, but is probably worth a shot.

---

### Post by Sasabune on 2007-07-22
You are all wrong. It is another ingenious feature of gnome that you are not worthy to use if you don't see its supreme usability.

---

### Post by ugm6hr on 2007-07-22
Catfish is pretty good as a GUI for find / locate:

[http://www.getdeb.net/search.php?keywords=catfish](http://www.getdeb.net/search.php?keywords=catfish)

I use it in Xubuntu, and integrate the search into thunar's right-click.  There's no reason why it shouldn't work just as well with Ubuntu.

---

### Post by saulysw on 2007-12-04
Ubuntus default search tool, IMHO, needs to be able to search subfolders in the GUI. Without this ability, it's basically useless. It should be the default behavior even.

---

### Post by aparigraha on 2007-12-11
> **ugm6hr said:**
> Catfish is pretty good as a GUI for find / locate:

[http://www.getdeb.net/search.php?keywords=catfish](http://www.getdeb.net/search.php?keywords=catfish)

I use it in Xubuntu, and integrate the search into thunar's right-click.  There's no reason why it shouldn't work just as well with Ubuntu.

CatFish using Xubuntu is great. Have been using it A LOT!

```
sudo apt-get install catfish
```

Then create a integrate-catfish.sh file, and paste this in there and save it.
```
#!/bin/bash
echo "Checking for $HOME/.config/Thunar/uca.xml ..."
if [ -e $HOME/.config/Thunar/uca.xml ]; then
	echo "Integrating Catfish into Thunar ..."
	CONTENT='
	<action>
		<icon>/usr/share/icons/Tango/scalable/actions/search.svg</icon>
		<name>Search</name>
		<command>catfish --fileman=thunar --path=%f</command>
		<description>Search this folder for files using Catfish</description>
		<patterns>*</patterns>
		<directories/>
	</action></actions>
	'
	cat $HOME/.config/Thunar/uca.xml >> newtmp
	sed 's/<\/actions>//' <newtmp >newfile
	echo $CONTENT >> newfile
	mv $HOME/.config/Thunar/uca.xml $HOME/.config/Thunar/uca.xml.bak
	mv newfile $HOME/.config/Thunar/uca.xml
	rm newtmp
else
	echo "Cannot found uca.xml, please configure UCA, in Thunar. [Click Edit, Configure custom actions..., OK] or create it manually!"
fi

```

Make the file executable and execute it. Next time you start your file browser right-click and search away!

---

### Post by Mlok on 2007-12-12
Hi

I had the same problem, and the best solution I have found is to use the "Search File" app in the "Shortcuts" Ubuntu menu (sorry if the names don't match, I'm on the French localization.)

Another way to reach this application is to launch gnome-search-tool from the terminal.

Hope this helps.

PS : the nautilus search tools seems counterintuitive & useless to me. Being such a key element in an operating system, I'm quite amazed. I hope this will be improved...

---

