---
title: "Cannot download files from Firefox browser web"
date: 2015-04-21
forum: Apple Hardware Users
---

### Post by caesar753 on 2015-04-21
Hello everybody,

i'm using lubuntu 14.04 on an old ibook G4 1.2 GHz and i'm experiencing this strange behavior of Firefox: when i try to download a file from a webpage (in particular i discovere it on Dropbox site , but then i realized it happens with every file i try to download) Firefox doesn't start the download and, when i see the Download page, it says "Failed"
Firefox version is 37.0.1 

thanks to everybody!

---

### Post by rican-linux on 2015-04-21
I may be with dropbox. I can upload/download from my google drive fine.

---

### Post by caesar753 on 2015-04-21
But it doesn't happen only on Dropbox site,but on every site ... 
But i discovered that sometimes the file is downloaded but the .part extension remains appended at the end... very, very strange...

---

### Post by luigiburdo on 2015-04-21
yes it is true firefox is buggy ... after donwload you need to rename the file ... just delete the .part extension

---

### Post by caesar753 on 2015-04-22
Thanks, is a problem of Firefox 37.0.1 or of Firefox IN PPC Ubuntu?

---

### Post by luigiburdo on 2015-04-22
i have this issue in Lubuntu . Before i was using mate and didt had this problems. i dont know if is a new version issue or a distro issue

---

### Post by caesar753 on 2015-04-26
But this firefox version ha a lot of bugs: 
- i cannot let Menu Bar and Bookmarks Toolbar show
- Firefox doesn't save passwords
- cannot use the search box (if i go to mozilla addons site i can install Google searchbox, but at next reboot the addon has been deleted)
- cannot use addons

Do you thing downgrading from 14.04 to 12.04 the system will be more stable and usable?

Thanks

---

### Post by luigiburdo on 2015-04-26
i m facing this issue on Lubuntu . On mate everything was working (in the firefox side) ... but the 14.4.1 is really unstable on mate and there is not intention to make a 14.04.2 of mate the 15.04 is not working right or better say is not working at all and our reports was not hear by the mate dev.

---

### Post by rican-linux on 2015-04-26
I as well am facing the same issues. I opened a bug in LP

---

### Post by caesar753 on 2015-04-27
Can you link your bug report, so i can support it? Thanks!

---

### Post by xeno74 on 2015-04-27
Hi All, 

I tested Firefox 37.0.2  on Lubuntu 12.04.5 PowerPC and on ubuntu MATE 15.04 PowerPC today. The search bar beside the URL field doesn't work. The  search field on the New Tab page doesn't work either. I have to use a  search engine directly. I can't copy a link with the right-click context  menu. 

Rgds, 

Christian

---

### Post by rican-linux on 2015-04-27
Please add and comment on to this bug report **[Bug #1448359]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1448359")**

---

### Post by luigiburdo on 2015-04-27
comment from as been add...
first bad mesa colors... now xorg... and firefox ... soon no linux at all... they are kill us ane oice a time :-(

---

### Post by rican-linux on 2015-04-27
luigi, i know what you mean. I still cannot believe that Jessie has bad support on the G5, when it works so well on the G4....

---

### Post by luigiburdo on 2015-04-28
because the g5 is full big endian and need optimization for it.. im pretty sure devs they are using a g4 or worst a qemu for make the bilding of systems. i didnt test jessie in qemu ppc 32 but im pretty it will work there... but in qemu 64 xorg crashlike the real hardware...

---

### Post by rican-linux on 2015-04-28
that needs to be fixed!

---

### Post by luigiburdo on 2015-04-28
> **rican-linux said:**
> that needs to be fixed!

Dont belive too much in it my friend...
nothing is more working ... we are going out totally ... in past powerpc devs was fighting now look like they loose all force.
i loose hope on everything about linuxppc on my great quad and the quad is a really capable machine today too.... after see the mate devs never release 14.04.2 and release mate 15.04 after our reports about the xorg issue.... i think our voice will not ear by no one.
Rightnow my video of mate on mini g4 have more than 2000 views .. it mean many people are interested on it ... and in g5 more then g4 ... but no one ear ... X86, Arm and EL cover all the time of devs

---

### Post by rican-linux on 2015-04-28
that is just sad

---

### Post by luigiburdo on 2015-04-28
yes really sed my friend ... 
i did many test for understand the limits and the performances of this machine ... and think about Ps3 with yld need 2,46 mins for boot win xp under qemu .... the quad only 1.12 ...

---

### Post by luigiburdo on 2015-04-30
I been reported it as post in the bug signed by rican

```

luigi@luigi-desktop:~$ firefox 

(process:2061): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
1430379834884    DeferredSave.extensions.json    WARN    Write failed: Error: Promise.all() expects an iterable. (resource://gre/modules/Promise.jsm -> resource://gre/modules/Promise-backend.js:521) JS Stack trace: Promise.all@Promise-backend.js:521:1 < postMessage@PromiseWorker.jsm:266:38 < TaskImpl_run@Task.jsm:314:40 < TaskImpl@Task.jsm:275:3 < createAsyncFunction/asyncFunction@Task.jsm:249:14 < Task_spawn@Task.jsm:164:12 < this.BasePromiseWorker.prototype.post@PromiseWorker.jsm:263:1 < post/<@osfile_async_front.jsm:421:25 < TaskImpl_run@Task.jsm:314:40 < TaskImpl@Task.jsm:275:3 < createAsyncFunction/asyncFunction@Task.jsm:249:14 < Handler.prototype.process@Promise-backend.js:870:23 < this.PromiseWalker.walkerLoop@Promise-backend.js:749:7 < this.PromiseWalker.scheduleWalkerLoop/<@Promise-backend.js:691:37
1430379834886    addons.xpi-utils    WARN    Failed to save XPI database: Error: Promise.all() expects an iterable. (resource://gre/modules/Promise.jsm -> resource://gre/modules/Promise-backend.js:521) JS Stack trace: Promise.all@Promise-backend.js:521:1 < postMessage@PromiseWorker.jsm:266:38 < TaskImpl_run@Task.jsm:314:40 < TaskImpl@Task.jsm:275:3 < createAsyncFunction/asyncFunction@Task.jsm:249:14 < Task_spawn@Task.jsm:164:12 < this.BasePromiseWorker.prototype.post@PromiseWorker.jsm:263:1 < post/<@osfile_async_front.jsm:421:25 < TaskImpl_run@Task.jsm:314:40 < TaskImpl@Task.jsm:275:3 < createAsyncFunction/asyncFunction@Task.jsm:249:14 < Handler.prototype.process@Promise-backend.js:870:23 < this.PromiseWalker.walkerLoop@Promise-backend.js:749:7 < this.PromiseWalker.scheduleWalkerLoop/<@Promise-backend.js:691:37


```

---

### Post by caesar753 on 2015-05-03
it's incredible: our issue is still unassigned and undecided...

---

### Post by Elfy on 2015-05-03
> **caesar753 said:**
> it's incredible: our issue is still unassigned and undecided...

Hardly incredible - it's marked as affecting ONE person. Marking a bug as affecting is NOT the same as commenting.

If this does affect more people, perhaps they should mark it as affecting them. 

Even so - there are hundreds of bugs that never get fixed.

---

### Post by bapoumba on 2015-05-03
Please understand I'm not much into Firefox inner guts :)
Would this issue be better taken care of in the mozilla bug tracker itself ?

When I searched for the reported errors :
[https://github.com/kriskowal/q/issues/616](https://github.com/kriskowal/q/issues/616) and [https://bugzilla.mozilla.org/show_bug.cgi?id=1104014](https://bugzilla.mozilla.org/show_bug.cgi?id=1104014)

---

### Post by xeno74 on 2015-05-03
> **Elfy said:**
> Hardly incredible - it's marked as affecting ONE person. Marking a bug as affecting is NOT the same as commenting.

If this does affect more people, perhaps they should mark it as affecting them. 

Even so - there are hundreds of bugs that never get fixed.

I added me to the affecting list.

---

### Post by rican-linux on 2015-05-04
More people need to add themselves as being effected. It is already a confirmed bug but still unassigned.

---

### Post by luigiburdo on 2015-05-04
Rican im redirecting all the ppl who are interested in LinuxPPc on MacMini g4 and on G5 from g+ and youtube here on ubuntuforums.org :-P i hope much will be much the devs will start belive in our Machines.

---

### Post by rican-linux on 2015-05-04
Thanks plus there a few good blogs out there promoting PPC hardware on Linux. The more the word gets out the more of chance support will continue.

---

### Post by xeno74 on 2015-05-15
Fyi:

> 
i had the problems described above on a mac mini g4 running precise.

Upgrading the firefox package to version 38 provided by the mozilla-
security ppa

[https://launchpad.net/~ubuntu-mozilla-security/+archive/ubuntu/ppa](https://launchpad.net/~ubuntu-mozilla-security/+archive/ubuntu/ppa)

solved the problems.

-- you received this bug notification because you are subscribed to the bug report. 


---

### Post by xeno74 on 2015-05-15
I can acknowledge that the problems were solved.

Firefox **38.0** on ubuntu MATE 15.04 PPC and on Lubuntu 12.04.5 PPC:

[[IMG]http://forum.hyperion-entertainment.biz/download/file.php?id=1731&t=1[/IMG]]("http://forum.hyperion-entertainment.biz/download/file.php?id=1731&mode=view") [[IMG]http://forum.hyperion-entertainment.biz/download/file.php?id=1732&t=1[/IMG]]("http://forum.hyperion-entertainment.biz/download/file.php?id=1732&mode=view")

---

### Post by rican-linux on 2015-05-15
Awesome! I was always under the impression that PPA did not work on PPC machines

---

### Post by xeno74 on 2015-05-15
> **rican-linux said:**
> Awesome! I was always under the impression that PPA did not work on PPC machines

I didn't install it via PPA yesterday. I did a normal update on ubuntu MATE 15.04 and Lubuntu 12.04.5.

---

### Post by rican-linux on 2015-05-16
someone in LP recommended using the PPA. This is why I asked.

---

