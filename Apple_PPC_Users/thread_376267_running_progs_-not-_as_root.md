---
title: "running progs -not- as root"
date: 2007-03-04
forum: Apple PPC Users
---

### Post by joneSi on 2007-03-04
All,

I've been around linux for a few years, coming and going with stints (almost always redhat and/or fedora core btw).  I've been able to install things in the past by fighting through it...but I forgot what I need to do here.

I am able to install AMSN, and if I try to run it when I am not root, it won't start up.  However, if I am in as root I can run it.  Obviously I don't want to be running things as root if I can help it.  I have tried to go as far in the install process as I can without switching to root.  Then finish the install...by the time I am done, I'm unable to start as my regular user.

Do I need to chmod or chown it?  

Where did I go wrong?  :confused: 

TIA
joneSi

---

### Post by aysiu on 2007-03-04
Go to [the terminal](http://www.psychocats.net/ubuntu/terminal).

Type ```
amsn
``` and then post the output back in this thread. Errors, non-errors... whatever spits out after you type that command.

---

### Post by joneSi on 2007-03-05
> **aysiu said:**
> Go to [the terminal](http://www.psychocats.net/ubuntu/terminal).

Type ```
amsn
``` and then post the output back in this thread. Errors, non-errors... whatever spits out after you type that command.



I'll gladly do this tonight.  I appreciate the input.

joneSi

---

### Post by joneSi on 2007-03-05
Here you have it...

```

 amsn
Error in startup script: error copying "langlist" to "/home/jonesi/.amsn/langlist.xml": permission denied
    while executing
"file copy -force "langlist" "$filename""
    (procedure "::lang::LoadVersions" line 20)
    invoked from within
"::lang::LoadVersions    "
    (procedure "scan_languages" line 6)
    invoked from within
"scan_languages"
    invoked from within
"if { $initialize_amsn == 1 } {
        ###############################################################
        create_dir $HOME
        create_dir $HOME/plugins
        create_di..."
    (file "config.tcl" line 1471)
    invoked from within
"source config.tcl      "
    ("uplevel" body line 23)
    invoked from within
"uplevel \#0 {

        source ctthemes.tcl
        source progressbar.tcl  ;# Progressbar Megawidget
        source migmd5.tcl
        source des.tcl          ;# DES encryption
        source s..."
    (procedure "reload_files" line 2)
    invoked from within
"reload_files"
    (file "/usr/bin/amsn" line 237)


```


thanks
joneSi

---

### Post by Auria on 2007-03-05
aMSN stores its info in a folder '/home/jonesi/.amsn/'.

apparently access to this folder is restricted, you should try changing perfmissions to this folder (BTW if it still doesn't fix it you could also aask on the aMSN forums they will know better)

---

### Post by aysiu on 2007-03-05
> **Auria said:**
> aMSN stores its info in a folder '/home/jonesi/.amsn/'.

apparently access to this folder is restricted, you should try changing perfmissions to this folder (BTW if it still doesn't fix it you could also aask on the aMSN forums they will know better)
Auria's right.

Try ```
sudo chown -R jonesi:jonesi /home/jonesi/.amsn
``` to make sure you have ownership of that folder.

By the way, it probably changed ownership *because* you ran aMSN as root. Read more here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by joneSi on 2007-03-05
Ok, so I'm not quite sure what I am reading, but I'm going to go back and read it again.  Instead of doing this (because I have even had issues after I changed the permissions) I went and got the dependent packages for galaxium and then did a dpkg install for that.  It is a great looking interface and IMO its better eye candy than aMSN.  So I am happy.

Thanks to those for their input here.  I need to go back and try now with the chown -R jonesi...


I'll be around here more now, thanks for the very warm welcome.

Now I need to start on getting my ibook trackpad to scroll :)

joneSi

---

### Post by Auria on 2007-03-06
> **joneSi said:**
> Ok, so I'm not quite sure what I am reading, but I'm going to go back and read it again. 

What did you not understand?

> got the dependent packages for galaxium and then did a dpkg install for that.  It is a great looking interface and IMO its better eye candy than aMSN.  So I am happy.

Thanks to those for their input here.  I need to go back and try now with the chown -R jonesi...


I'll be around here more now, thanks for the very warm welcome.

Now I need to start on getting my ibook trackpad to scroll :)

joneSi



Unfortunately Galaxium doesn't even have display pics and file transfers if i understand their website properly.

For eye candy, aMSN 0.97 will be much better than the current, i'm already using it from SVN (programmer's development version)

---

### Post by joneSi on 2007-03-06
> **Auria said:**
> What did you not understand?





Unfortunately Galaxium doesn't even have display pics and file transfers if i understand their website properly.

For eye candy, aMSN 0.97 will be much better than the current, i'm already using it from SVN (programmer's development version)


Where I was reading the file permissions parts, I'll go back through.

I've just removed it [aMSN] for now.  I have little to no interest in file transfers and showing pictures.

I'll give it a go in a few minutes or tomorrow.  I am currently backing up my iTunes purchased library.

joneSi

---

