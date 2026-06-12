---
title: "removing programs"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by Tucatts on 2007-04-27
I am trying to remove and reinstall AVG antivirus. Synaptic Package manager finds the avg program and I mark it for complete removal. Then I get an error 150 and it all stops. Is there another way to remove a program like this? Feisty is doing great, just trying a bunch of stuff still learning. 
Thanks in advance

---

### Post by Cypher on 2007-04-27
Does Applications->Add/Remove do any better removing the application? 

If not, open up a terminal and do
```

dpkg -l | grep avg

```
and
```

dpkg --remove <avg-package-name>

```

---

### Post by diskotek on 2007-04-27
edited: there is a better advice now :D

---

### Post by Tucatts on 2007-04-27
Almost but not quite. Actually I got a script that said the program was not installed but it is. Still in Applications/system tools and it will open when I click on the AVG icon.  Interesting. figuring this stuff out is kinda like doing a sudoku puzzle lol. Any other suggestions?
Many thanks

---

### Post by zvacet on 2007-04-27
```
sudo apt-get remove --purge program_name
```

program_name = exact name of your Avg

---

### Post by mikewhatever on 2007-04-30
Try this how-to [http://ubuntuforums.org/showthread.php?t=426070&highlight=avg](http://ubuntuforums.org/showthread.php?t=426070&highlight=avg)

---

