---
title: "remove symlink"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by beamo on 2007-01-13
I'm having a problem removing a link I placed on my desktop. It was created using the file browser as root. I right clicked the program which was in /usr/bin and created a link and then dragged it to the desktop. I'd like to get rid of it now but nothing seems to work. I've tried to delete it from the filebrowser as "root" but it is saying that it is on a different filesystem. How do I delete this thing?

---

### Post by blackened on 2007-01-13
In the terminal try
```
sudo unlink name_of_link
```
then try to delete the link file (not the file in /usr/bin).

---

### Post by steve.horsley on 2007-01-13
I don't understand your problem there, but if you are having trouble with the GUI, try this command:
sudo rm /home/username/Desktop/filename

---

