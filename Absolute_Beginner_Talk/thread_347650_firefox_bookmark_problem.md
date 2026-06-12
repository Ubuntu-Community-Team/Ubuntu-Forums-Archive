---
title: "firefox bookmark problem"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by cypher_666 on 2007-01-27
i just came to my machine to check something online and i opened up firefox and all my bookmarks have suddenly dissapeared, my cookies are still intact as my usernames etc are still saved for websites.

ive tried to search my hard drive but to no avail.

has anyone else had this problem before?

thanks in advance.

---

### Post by fsando on 2007-01-27
I haven't seen that myself - and it sounds a bit strange. It could be that you have accidentally created more than one profile and are now using a different one (This wouldn't explain why you have retained your cookies though). 
Have you looked in
/home/<your name>/.mozilla/default/<your profile> .
for the file bookmarks.html? All your bookmarks are kept in that file. 

Remember that files and folders starting with a period are hidden so your .mozilla folder will be hidden.

To see hidden files in nautilus: View > Show Hidden Files.

---

### Post by cypher_666 on 2007-01-27
fantastic, god i love this place.

they are all there, i have no idea why it hasnt showed up as i only have one profile according to the folders, but i just imported them and there they are :)

thanks very much.

---

### Post by fsando on 2007-01-27
A pleasure to help :)

---

