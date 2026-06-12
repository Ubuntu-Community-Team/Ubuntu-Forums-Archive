---
title: "login problems; user don't exist"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by acjosefsen on 2008-02-22
I installed ubuntu almost a week ago and has been using it. For example did I trnaslate a manuscript, so I really don't want to do anything that could erase what I've done so far.
But when I write my username and password it tells me: "Your home directory is listed as: '/home/ac' but it does not appear to exist. Do you want to log in with the / (root) directory as your home directory? It is unlikely anything will work unless you use a failsafe session."
Then I press 'Yes', and it tells me following: 
"Users $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. Users $HOME directory must be owned by user and not writable by other users.
I press 'OK' (which is the only option)
Now it tells me: "Your session onæy lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of discspace. Try logging in with one of the failsafe sessions to see if you can fix this problem."
I have the option to view more details, but it doesn't help me.
I opened the failsafe session and then I don't know what to write.
I hope to get a step-by-step answer, 'cause I'm getting more and more frustrasted by this ubuntu.

---

### Post by Cypher on 2008-02-22
Did you change anything to make Ubuntu go from working to not?

Can you boot into the (Recovery Console) option in GRUB and then be given the prompt? If so,  see if your home directory exists with
```

ls /home/ac

```
Then check what shell you are using with
```

cat /etc/passwd | grep ac

```

---

