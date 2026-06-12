---
title: "&quot;You have new mail&quot;"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by shodson on 2006-09-12
When I SSH into my Ubuntu 6.06 server it says "You have new mail".  How do I read this mail from a command line?  Where is the mail stored?  Is there a command-line mail reader that I can use?

---

### Post by cstudent on 2006-09-12
There are several. I prefer mutt.

---

### Post by Timothy Butwinick on 2006-09-12
Mutt is not initially installed:

```
sudo apt-get install mutt
```

---

### Post by blakesmith on 2006-09-12
Type "mail" and it should come up, "q" to quit.

---

### Post by shodson on 2006-09-12
> **blakesmith said:**
> Type "mail" and it should come up, "q" to quit.

NOPE

-bash: mail: command not found

---

### Post by shodson on 2006-09-12
> **Timothy Butwinick said:**
> Mutt is not initially installed:

```
sudo apt-get install mutt
```

Thanks, that works.  I just had a few messages from a cron job.

---

### Post by blakesmith on 2006-09-12
Hmm, I'm thinking that didnt work because you are SSHed into the server... mailx is a base package.

---

### Post by Timothy Butwinick on 2006-09-12
Shodson, you can also choose to install 'mail' instead of mutt (not that is necessary, or even any use at all, to have them both: use whichever you like):

sudo apt-get install mail

You can remove the unwanted one using 

sudo apt-get remove <mail or mutt>

---

### Post by Timothy Butwinick on 2006-09-12
> **blakesmith said:**
> mailx is a base package.

Oh. Sorry for my reply about installing mail. (How do I delete messages?)

---

### Post by blakesmith on 2006-09-12
I saw a Mod tell someone that there was a delete post option when you go to edit your own post, but I never saw one... so I don't know, sorry.

---

