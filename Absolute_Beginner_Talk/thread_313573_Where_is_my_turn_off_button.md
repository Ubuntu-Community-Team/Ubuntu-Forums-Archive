---
title: "Where is my turn off button?????/"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by fasoulas on 2006-12-06
I can't see my turn off button i can only see hibernate log off lock screen switch user but nowwhere the button that suts down the pc 

I can only shut it down by entering poweroff command in terminal 

What happend???

---

### Post by Sef on 2006-12-06
somehow you lost the button.

In the mean time, if you are running Ubuntu, you can shut down via the terminal.  (Applications > Accessories > Terminal)

Type this code in to shut down:

```
sudo halt
```  

or

```
sudo shutdown -h now
```

---

### Post by fasoulas on 2006-12-06
> **Sef said:**
> somehow you lost the button.

In the mean time, if you are running Ubuntu, you can shut down via the terminal.  (Applications > Accessories > Terminal)

Type this code in to shut down:

```
sudo halt
```  

or

```
sudo shutdown -h now
```

But i want that button back i don't want the commands

---

### Post by bscbrit on 2006-12-06
I've also seen this problem before.  However, if you select 'Log Off' from your user area, you are able to select 'Shut Down' from the log on screen that subsequently appears.  

In my case, the next time that I logged on, my missing button mysteriously reappeared.

---

### Post by fasoulas on 2006-12-06
OK i think i found the problem so i thing it is a good way for others to learn from my mistake

It is simple,Last night i was testing a few login screens and i must have changed the settings about sessions

---

### Post by cmapesjr on 2007-01-21
Make sure "ask on logout" is checked in sessions.


Cheers

Had the same problem too!

---

### Post by mkjarema on 2007-06-06
where is the "sessions" section?
THX

---

### Post by steeleyuk on 2007-06-06
> **mkjarema said:**
> where is the "sessions" section?
THX

System > Preferences > Sessions

---

### Post by mkjarema on 2007-06-06
thanks, i had removed the sessions menu from the main menu.  Now, I don't see in any of the tabs a place to check to show shut down button.....
suggestions.....

I am using Feisty
***fixed it!**** THANK YOU

---

