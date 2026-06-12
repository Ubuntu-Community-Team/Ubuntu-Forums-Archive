---
title: "XFer settings, configurations, &amp; bookmarks"
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by Cousindaddy on 2006-02-18
Unfortunately, all of my settings, bookmarks and configurations are assigned to root.  How can I transer these to a different user?  thx

---

### Post by Joeb on 2006-02-18
You could copy the appropriate directories to your user or home directory and then change the ownership of them to your user id.  If they are already in your home directory, then you just need to change ownership with the following command:

sudo chown -R  user-id directory

So if your username were Tom and you wanted your firefox to be changed back to your ownership you would issue the following command from the command line while in your home directory:

sudo chown -R Tom .mozilla

(The -R tells the command to work change every file below the .mozilla directory)

Since this is in the "Beginners Forum"  I should caution you to be careful when using the chown command outside your home directory as you can cause things to quit working.  Also, for more info on the chown command, issue the command:  man chown     from the command line.

Joeb

---

