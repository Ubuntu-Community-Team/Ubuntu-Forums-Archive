---
title: "GDM disaster - help!"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by lalji on 2007-06-11
I can't log in at the regular username/password prompt when I boot Ubuntu (feisty fawn). Here's the error message:

"GDM could not write to your authorization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case, it is not possible to log in. Please contact your system administrator."

There's plenty of disk space, so that isn't the problem. I'm the system admin (gulp), which isn't much help... so here's hoping you might have good suggestions :-)

Prior to this problem, firefox had crashed (from some travel websites). I forced it to quit, then Evolution acted up and started saying there wasn't enough disk space. I rebooted, and then the above message. I can access the prompt if I boot in safe mode, but am not particularly proficient with it.

Thanks in advance.

---

### Post by taurus on 2007-06-11
Are you sure you have space on /?  Boot into recovery mode from GRUB menu and post the output of this command here.

```
df -h
```

---

### Post by ryanVickers on 2007-06-11
Mmm, doesn't sound good - reminds me of something that eventually drove me to a reinstall!

Now that your reassured, :p Try booting up in recovery mode - oh, you did that, didn't see.  I would try do look around for help on disabling use of the authorization files, I've found this sometimes helps; they just provide an unnecessary nuisance anyways, I would disable them, all the expert say they're redundant old code!

---

### Post by lalji on 2007-06-12
taurus was right, my / was 100% used. I went back into the prompt and found some files to delete, and now I'm back in Ubuntu and will take care of my filespace issues. (not very clever of me to begin with).

Thank you.

---

### Post by rfurman24 on 2007-06-12
I have accidentally let / get full before. Now I make sure it has way more space than I can possibly use in /.

---

### Post by ryanVickers on 2007-06-12
Glad to know you found a solution!  Seems odd though, I thought ubuntu reserves a little bit in the / or root (whichever) section so that this doesn't happen?...

---

### Post by taurus on 2007-06-12
> **ryanVickers said:**
> Glad to know you found a solution!  Seems odd though, I thought ubuntu reserves a little bit in the / or root (whichever) section so that this doesn't happen?...

5% of your total disk space is reserved (ext3).  That's why you can still boot Ubuntu even if / is 100% full.  Otherwise, you would be a dead duck.

---

### Post by ryanVickers on 2007-06-12
Yeah, that's what I thought, so it seems strange this problem would occur!

---

