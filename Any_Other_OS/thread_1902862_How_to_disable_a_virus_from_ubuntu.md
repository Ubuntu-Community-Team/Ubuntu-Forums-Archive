---
title: "How to disable a virus from ubuntu?"
date: 2012-01-01
forum: Any Other OS
---

### Post by fardin97 on 2012-01-01
Hi,I am a ubuntu user.before ubuntu i used win 7.bt i changed from windows for 1 reason.and that was virus.when the virus first attacked I did not understand what happened.I just found some files named readme.eml .I deleted them all but still windows kept on making them.then 1 day all the exe files in my laptop became corrupt.i could not start any exe files.i re-installed windows for 4 or 5 times but still the exes won't run.then i understood that my laptop has been attacked.I then deleted all the exes using a antivirus because the antivirus shows those as chir.b virus.then that day after re-installing windows again i could not start windows.only the  laptop boot logo comes and then a dash that means windows is loading from hard disk comes.and the pc just freezes there.nothing happens.i left my laptop on for 6 hours but the "windows is loading" thingy doesn't come.then I installed Ubuntu cause i knew that Ubuntu doesn't run any windows virus or just ignores them.from then i started using ubuntu.but then i found a lot of readme.eml files in my pc.They are like everywhere.i deleted them using clamav but they kept on making.also on clamav all my exe files are shown as chir.b virus.how can i solve this problem and get back to windows?i know gnome 3 is beautiful but i need windows for gaming and gaming is slow in wine.pls reply quickly.

P.S. Sorry if i posted in the wrong section cause I can't understand where to post about virus problem and sorry for any mistake

thanks in advance!!

---

### Post by syerges on 2012-01-01
You need to format everything and start fresh with everything. Something you are keeping has the main virus causing all of these files.

---

### Post by fdrake on 2012-01-01
back up the data that you need and start with a fresh install.

---

### Post by LinuxFan999 on 2012-01-01
This sounds like a very strange issue.

Try Using Darik's Boot and Nuke to erase the hard drive completely.
Next, use the Gparted Live CD to create a new partition table.
Then boot from the Windows installation DVD and reinstall Windows.

Get Darik's Boot and Nuke here: [http://www.dban.org](http://www.dban.org)

Get the Gparted live CD here: [http://gparted.sorceforge.net/livecd](http://gparted.sorceforge.net/livecd)

---

### Post by vpharry on 2012-01-01
INstall everything afreash... and I suggest that you get rid of windows or atleast install a good antivirus

---

### Post by elliotn on 2012-01-01
its rude to say they must format their windows, no just install avast AntiVirus in safe mode and set avast to a boot scan so next time it would scan on boot while all Windows file are on sleep

---

### Post by syerges on 2012-01-01
not every virus is covered in anti-virus software. If this one is changing his .exe files and extensions of other files, it is not only super dangerous, but his system will never recoup if an anti-virus even finds the culprit because it won't be able to change the files back. I wouldn't suggest a wipe if it wasn't changing file extensions.

---

### Post by fdrake on 2012-01-01
> **elliotn said:**
> its rude to say they must format their windows, no just install avast AntiVirus in safe mode and set avast to a boot scan so next time it would scan on boot while all Windows file are on sleep
what good would bring installing an anti virus after your files have been corrupted and maybe the virus code is embedded at the beginning of the boot program! that doesn't give any warranty it will work and for sure it wont recover the corrupted files. 

We don't know what kind of damage the virus may have done.

---

### Post by chipbuster on 2012-01-01
Something doesn't quite add up here. You say you reinstalled several times (at least 5) but it kept coming back. Did you format the drive on any of the reinstalls? If you did, this is one insane piece of malware or your install disc is infected, because reinstalling with a format is supposed to be the only only completely guaranteed method of rootkit removal (and it should take out other viruses/trojans as well)

[http://technet.microsoft.com/en-us/library/cc512642.aspx]("http://www.computerworld.com/s/article/9218062/Microsoft_clarifies_MBR_rootkit_removal_advice")

> I then deleted all the exes using a antivirus because the antivirus shows those as chir.b virus

Do you remember the name of the antivirus you used? There's a lot of malware out there masquerading as antiviral programs (my sister caught one a few days ago) and they just infect your system even more if you give them administrator access to "remove" viruses.

--------------------------------------------

To LinuxFan999, would a variant "dd if=/dev/zero of=/dev/sda1" work to wipe the hard drive? I've used that a few times to destroy a bunch of partitions I couldn't be bothered to remove normally.

---

### Post by fardin97 on 2012-01-01
@all who suggested to wipe the whole hard drive,i don't want to delete any of the files in my other partition.because they are all important.and the size of them is about 1 tb.

@chipbuster,I formatted the whole c drive(windows drive)and reinstalled everytimes but still the virus came back.
and I used Kaspersky 2012 and it worked only one time.but the second time it showed the problem like the other exe files

@everyone, sorry for not mentioning this but the problem showed that 

"the name.exe file could not be started or not responding"
and the problem detail shows that "APPCRASH.exe" and it's not the exe that i opened.

@elliotn, i used the kaspersky,bitdefender,avast safemode antivirus but they did not work.

also @those who did not understand my question,the virus is still working in ubuntu and makes readme.eml everyday.

---

### Post by fdrake on 2012-01-01
> also @those who did not understand my question,the virus is still working in ubuntu and makes readme.eml everyday
how did you install ubuntu? with wubi or you created a new partition? sorry but how could we know all these details in the first place.. it's not implicit from your first post!
anyway if the virus is working even in ubuntu something is not right, if you are using a partitioned install

edit:[http://answers.ask.com/Computers/Programming/what_is_an_eml_file](http://answers.ask.com/Computers/Programming/what_is_an_eml_file)
> 
What is An Eml File?
	
atajay: This file type is used to store saved e-mails from Microsoft's Outlook Express, but can be used by other e-mail clients. This file type can easily be infected so one should run a virus scan on eml files before trying to open the file.


---

### Post by syerges on 2012-01-01
The only thing that makes sense to me is that one of those precious files you can't delete contains this virus that causes these things to happen. Every time you open up that file, it will do it's dirty deed. Is there a file you are keeping that you open regularly when these things occur?

---

### Post by Elfy on 2012-01-01
Thread moved to Other OS/Distro Talk.

---

### Post by Myrddin Emrys on 2012-01-01
Your Windows malware can't be running under Linux, so none of this is an Ubuntu problem. One thing you might try is booting from the Avira rescue CD, which is a self-contained Linux-based system with an up-to-date virus scanner. Burn the ISO to CD on an uninfected system:

[http://www.avira.com/en/support-download-avira-antivir-rescue-system](http://www.avira.com/en/support-download-avira-antivir-rescue-system)

and follow the instructions. You might then be able to clean the infection from all of your hard disk partitions.

It's not clear why you keep getting re-infected. If it's some sinister virus that gets into the boot sector all bets are off. But it may just be coming from some of the files you want to keep, or via email (you give the name of an 'email worm'. Chir.B,  above - if infected emails are on your provider's server they need to be purged). If you have a working Windows system, the best approach would be to join a specialised anti-malware forum, where trained volunteers will lead you through the process of cleaning your system:

[http://www.bleepingcomputer.com/combofix/how-to-use-combofix#forums](http://www.bleepingcomputer.com/combofix/how-to-use-combofix#forums)

Under their supervision, you will be asked to use specialised tools like ComboFix, which you should NOT try to run on your own (they can do much more harm than good if run at the wrong time, or with the wrong settings). You'll get the best response with a clear and well-formatted description of the problem (and by following their posting rules). You'll need to be patient - there are usually many more people asking for help than volunteers!

Once you have a clean system, you can reduce the risk of further infections by:

- Not opening unknown email attachments!

- Turning on Windows Update for automatic OS updates

- Keeping other software up to date with Secunia PSI:
[http://secunia.com/vulnerability_scanning/personal/](http://secunia.com/vulnerability_scanning/personal/)
(and switch on any auto updates provided by individual programs)

- Browsing in Firefox with NoScript and Web of Trust installed:
[https://addons.mozilla.org/en-US/firefox/addon/noscript/](https://addons.mozilla.org/en-US/firefox/addon/noscript/)
[https://addons.mozilla.org/en-US/firefox/addon/wot-web-of-trust/](https://addons.mozilla.org/en-US/firefox/addon/wot-web-of-trust/)

- Using a decent antivirus, like Avira:
[http://www.avira.com/](http://www.avira.com/)

- Running regular scans with Malwarebytes:
[http://www.malwarebytes.org/](http://www.malwarebytes.org/)

Or just installing Ubuntu...

---

### Post by Helen McCall on 2012-03-19
> **fardin97 said:**
> @all who suggested to wipe the whole hard drive,i don't want to delete any of the files in my other partition.because they are all important.and the size of them is about 1 tb.

@chipbuster,I formatted the whole c drive(windows drive)and reinstalled everytimes but still the virus came back.
and I used Kaspersky 2012 and it worked only one time.but the second time it showed the problem like the other exe files

@everyone, sorry for not mentioning this but the problem showed that 

"the name.exe file could not be started or not responding"
and the problem detail shows that "APPCRASH.exe" and it's not the exe that i opened.

@elliotn, i used the kaspersky,bitdefender,avast safemode antivirus but they did not work.

also @those who did not understand my question,the virus is still working in ubuntu and makes readme.eml everyday.

Are you running the same games in wine on Ubuntu? If so you are probably running corrupted .exe files the same as you had for Windows.

---

### Post by husnos on 2012-03-25
and it is better to have two separate computers. one for windows and gaming. and another for linux an productivity. fixing an operating system is time consuming.

---

### Post by donkyhotay on 2012-03-27
> **syerges said:**
> the only thing that makes sense to me is that one of those precious files you can't delete contains this virus that causes these things to happen. Every time you open up that file, it will do it's dirty deed. Is there a file you are keeping that you open regularly when these things occur?

+1

---

