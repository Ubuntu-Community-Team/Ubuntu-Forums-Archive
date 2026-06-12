---
title: "I accidentally ended java process! Help!"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by xiaooaix on 2008-02-26
I saw that the java process was taking up a crapload of memory and did the stupid default Windows user thing and closed it. Now I can't get Azureus to work. 

So basically is there a way to fix this?

---

### Post by mwanstall on 2008-02-26
Restarting Azureus doesn't work? Restarting the computer? One of those is bound to work.

---

### Post by ntetreau on 2008-02-26
If it doesn't, start azureus in a terminal windows and copy the error message here

---

### Post by xiaooaix on 2008-02-26
Restarted azureus.
Restarted computer.
Tried both again.

Ok, started from terminal, it started up.

```
sudo azureus
Looking for and picking a preferred Java runtime
Use environment AZUREUS_JAVA to override
Using Java: /usr/lib/jvm/java-7-icedtea/jre/bin/java
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'


```

---

### Post by xiaooaix on 2008-02-26
It still won't start the actual program. Just from the terminal.
And the java process won't start back no matter how much I reset :/

---

### Post by xiaooaix on 2008-02-26
Through further investigation, when I start Azureus, so does the java process. But as soon as I press the "my torrents" tab, it just closes, along with the java process. 

Would a re-install of azureus fix this you think?

---

### Post by PmDematagoda on 2008-02-26
Did you try using a different Java Runtime Environment such as Java 6?

---

### Post by xiaooaix on 2008-02-26
> **PmDematagoda said:**
> Did you try using a different Java Runtime Environment such as Java 6?

How? I've only had Ubuntu a couple days.

---

### Post by PmDematagoda on 2008-02-26
> **xiaooaix said:**
> How? I've only had Ubuntu a couple days.

Install Java 6 using:-
```
sudo apt-get install sun-java6-jre
```
Then instruct Ubuntu to use Java 6 as default using:-
```
sudo update-alternatives --config java
```

---

### Post by xiaooaix on 2008-02-26
Got it, thanks :)

---

### Post by ntetreau on 2008-02-26
Looking at your terminal output, I see you were starting azureus using sudo.  There is a good chance you did this just to test but just in case, running applications as root or using sudo is a major security risk, especially for networked applications.  You should always assume that a broken application that only runs as root, is still a broken application and should be fixed or not used as is.

---

### Post by PmDematagoda on 2008-02-26
> **ntetreau said:**
> Looking at your terminal output, I see you were starting azureus using sudo.  There is a good chance you did this just to test but just in case, running applications as root or using sudo is a major security risk, especially for networked applications.  You should always assume that a broken application that only runs as root, is still a broken application and should be fixed or not used as is.

Big +1, I did not see that myself and I am ashamed of it:(. Thank you for pointing that out ntetreau.

---

