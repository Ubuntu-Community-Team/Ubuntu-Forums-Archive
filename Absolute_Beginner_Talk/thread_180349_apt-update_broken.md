---
title: "apt-update broken?"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by KevNice on 2006-05-22
I ran sudo apt-get update and at the end get this message:

Reading package lists... Done
W: GPG error: [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems


seems like a bit of a catch-22.

how do I fix this?

thanks

---

### Post by joshbax on 2006-05-22
i am a linux n00b and have just tried to get WNE working, having only got ndiswrapper workingg last night for my wifi, but i am trying to get WNE from both teh repositories and synaptic using the exact instructions on WINE's site, and i am getting no respons.
apt-get update is throwing up blanks too, saying the wine repositories are not there, or a same error message as to you, KevNice.

Is something big down?

---

### Post by dmizer on 2006-05-22
[QUOTE=KevNice]W: You may want to run apt-get update to correct these problems[/QUOTE]
your answer is in your question.  all you have to do is run apt-get update again.  it sometimes happens when a repository doesn't respond right away.

---

### Post by Mustard on 2006-05-22
There are various issues that could be causing this problem.  The purpose of the gpk keys is to ensure that you are downloading software that hasn't been tampered with.  The difficulty with this type of error is that, although you can simply ignore it and install whatever applications you want, you can't do it with any confidence that something is not amiss in the repository ie there could have been a security breach and malicous software could potentially be in the repositories.  

The error can occur for simple reasons like a problem connecting to a certain repository, and that can often be fixed by repeating the update process until the error doesnt occur.  

Another method is to go into Synaptic and set the gpg keys back to the default settings.  

Another method is to backup your old sources.list temporarily, totally blank the current sources.list file, then run apt-get update on the empty sources.list, then replace the source.list with the backup you just made, and apt-get update again.  

Another solution is to do this command below, which will delete some relevant files and the gpg keys and start from fresh..

```
sudo rm /var/lib/apt/lists/*Release*
```

---

### Post by KevNice on 2006-05-28
hmmm.. thanks for replying, but I left town for a few days and when I came back, I did just apt-get update again normally and it worked fine. Maybe something was down for a while..

---

