---
title: "Help creating desktop launcher"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by Beastie Boy on 2007-04-18
I have installed a Java application under Ubuntu 6.10 as per the instructions [here]("http://www.interactivebrokers.com/en/control/systemstandalone.php?os=unix&ib_entity=llc"). The app is in /home/paul/IBJts.

To run the app from the terminal I enter```
 cd IBJts
```

followed by ```
java -cp jts.jar:pluginsupport.jar:jcommon-1.0.0.jar:jfreechart-1.0.0.jar:jhall.jar:other.jar:rss.jar -Xmx256M jclient.LoginFrame .
```

I have to navigate to the IBJts to run the last command for it to work.

Could anyone please tell me how I could create a desktop icon to launch the app?

Cheers, Beastie.

---

### Post by RomeReactor on 2007-04-18
Hi. Let's try this: Right-click on the desktop and select "Create Launcher", name it, and on the "Command" section, enter

```
sh -c "/home/paul/IBJts && java -cp jts.jar:pluginsupport.jar:jcommon-1.0.0.jar:jfreechart-1.0.0.jar:jhall.jar:other.jar:rss.jar -Xmx256M jclient.LoginFrame ."
```

---

### Post by Beastie Boy on 2007-04-18
That almost worked. When I ran the launcher, nothing happened. I pasted the text into a terminal and it gave a "No permission" error (or something similar).

I changed the command to: ```
sh -c "cd IBJts && java -cp jts.jar:pluginsupport.jar:jcommon-1.0.0.jar:jfreechart-1.0.0.jar:jhall.jar:other.jar:rss.jar -Xmx256M jclient.LoginFrame ."
```
and that worked.
Many thanks for your help.

Cheers, Beastie.

---

