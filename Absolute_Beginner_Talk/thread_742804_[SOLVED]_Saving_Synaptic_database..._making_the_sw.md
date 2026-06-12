---
title: "[SOLVED] Saving Synaptic database... making the switch to 8.04 easier"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by cisforcojo on 2008-04-02
I've been wondering lately if there's a way to save the synaptic database so that when I do a clean install to 8.04, after the installation is done, it can compare the newly installed system to my old system (which programs I had installed) and then go about installing all of those. Of course, the ones I can't get that aren't in repos (like [www.getdeb.net](www.getdeb.net)) would be reported to me and I could go look for them manually. 

Is there such a thing?

---

### Post by kellemes on 2008-04-02
> **cisforcojo said:**
> I've been wondering lately if there's a way to save the synaptic database so that when I do a clean install to 8.04, after the installation is done, it can compare the newly installed system to my old system (which programs I had installed) and then go about installing all of those. Of course, the ones I can't get that aren't in repos (like [www.getdeb.net](www.getdeb.net)) would be reported to me and I could go look for them manually. 

Is there such a thing?

Try the following from terminal..
It will generate a file (mypackages) with your packages installed..
```
dpkg --get-selections | grep -v deinstall > mypackages
```

---

### Post by cisforcojo on 2008-04-02
Great! What about the compare part? :)

I was thinking of making a python script for this but I don't want to reinvent the wheel if I don't have to.

---

### Post by kellemes on 2008-04-02
Well, you could create the same list from the newly installed system and use "diff" two compare the 2 files like so..

```
diff file1 file2
```
It will show you the lines that are different.
Expect the list to be big..

Edit: By the way.. you won't be able to get an exact copy obviously, you'll be running a different os.
I'd use google to search for "saving your packagelist on Ubuntu" etc.. there maybe are better ways to do this..

---

### Post by cisforcojo on 2008-04-02
Found. Thanks for the help!
[http://duggmirror.com/linux_unix/Ubuntu_tricks_how_to_create_a_list_software_and_use_it_to_restore_your_pc/](http://duggmirror.com/linux_unix/Ubuntu_tricks_how_to_create_a_list_software_and_use_it_to_restore_your_pc/)
[http://ubuntuforums.org/showthread.php?t=479071](http://ubuntuforums.org/showthread.php?t=479071)

---

