---
title: "[SOLVED] /home partition killed Evolution"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by therandman on 2008-03-02
I have used the psychocats procedure for making a seperate /home partition on many computers with Feisty, this was the first time I tried it on 7.10.  I ended up losing all my custom settings, which I fixed by re-copying the hidden directories over to my new /home.  However, evolution won't cooperate with me, when I open it it acts like its the first time using it.  Is there something I need to do to make it work?

I had to upgrade since I had killed my Feisty installation (and I lost my original /home, so I'm starting over.)  I really don't want to lose all my recent emails again...

---

### Post by iris-n on 2008-03-02
After using that guide (actually, the command-line version) my evolution acted weirdly too, but 'twas only a matter of restarting it to make it find my mail.

Anyway, it's stored at /home/*yourname*/.evolution/mail/local
Check if all the files are there.

---

### Post by therandman on 2008-03-02
Thanks, I went ahead and went through the initial setup real quick.  All my email is there, but I'm going to have to reset up preferences for the accounts.  Luckily I didn't lose the mail.

---

### Post by The Cog on 2008-03-02
Evolution is a bit (lot) stupid, and stores lots of absolute pathnames in its configuration files. So if the name of your home directory changed, you are going to have a hard time finding and fixing all evolutions configuration files.

As far as I know, if your home path hasn't changed then as long as you can find all the configuratino files and copy them to hte new home, things should still work.

---

