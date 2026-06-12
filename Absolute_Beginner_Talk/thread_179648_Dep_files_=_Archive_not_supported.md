---
title: "Dep files = Archive not supported"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2006-05-20
I have been trying to download extra apps for ubuntu that are not in the repositries such as skype or one of the many alternatives Ekiga. The problem is that every *.dep file I download I can't open. The error I recieve:
> could not open file, Archive not supported

Even when I  used the terminal I get this:
> rudolf@Rudolf:~$ sudo dpkg -i skype.dep
dpkg: error processing skype.dep (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 skype.dep
rudolf@Rudolf:~$ ls
Desktop  my documents  Pictures  skype.deb
rudolf@Rudolf:~$

And notice, in the list the file is there! 

I have downloaded 5 different deb files from diffrent sites and still same result.
What now?

-=Thanks for the help people, I really appreciate it!=-

---

### Post by meng on 2006-05-20
Did you notice you misspelled skype.deb?

---

### Post by RudolfMDLT on 2006-05-20
[QUOTE=meng]Did you notice you misspelled skype.deb?[/QUOTE]

](*,) 

Fixed typo, still got the problem in the shell though... and was in formed:

> dpkg: dependency problems prevent configuration of skype:
 skype depends on libqt3-mt | libqt3c102-mt (>= 3:3.3.3.2); however:
  Package libqt3-mt is not installed.
  Package libqt3c102-mt is not installed.
 skype depends on libstdc++5 (>= 1:3.3.4-1); however:
  Package libstdc++5 is not installed.
dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured

This I should be able to sort out or find the answer in some other post, while searching for VOIP apps I did stumble across a similar problem. 

I should be able to install it now, but is there any reason why not any of the deb files will be configured in the shell? I don't mind using the textbase shell or the terminal, I just want to know whether there's something wrong with my system?
it does open tar.gz files...

Feeling quit stupid but thankful! - Thanks!

---

### Post by meng on 2006-05-20
Okay well you're making progress. You should install libstdc++5. As for the libqt issues, you need to edit the dependencies part of the package to bypass this, because ubuntu comes with differently labeled libraries (someone correct me if the terminology is wrong, the basic concept is approximately right though). There should be a step-by-step answer in the wiki or elsewhere in this forum. If all else fails, I have the repackaged ubuntu-compatible deb that I can send to you.

---

### Post by RudolfMDLT on 2006-05-21
[QUOTE=meng]Okay well you're making progress. *** There should be a step-by-step answer in the wiki or elsewhere in this forum. If all else fails, I have the repackaged ubuntu-compatible deb that I can send to you.[/QUOTE]

Thanks for the help! I'll give the wiki a try and the forum-they haven't failed thus far!- and if all else fails i'll contact you about emailing the dep file! Thank you very much, your help is very appreciated!:D

---

### Post by RudolfMDLT on 2006-05-21
Brilliant! Works like charm! Thnx!

---

### Post by meng on 2006-05-21
Glad to hear things worked out. And remember, think deb as in debian, NOT dep as in ... dependency?

---

