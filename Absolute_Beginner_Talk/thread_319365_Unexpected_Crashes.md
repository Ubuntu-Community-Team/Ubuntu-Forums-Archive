---
title: "Unexpected Crashes"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by mells on 2006-12-15
Right longshot here guys.

I'm running edgy 6.10 on a Compaq Evo N1020v notebook. I've been running it for a week without any problems at all, the installation of ubuntu was effortless and I really like working with it.

However, for the past few days I have had system crashes without warning. Nothing running at all, but as the system comes up it will just hang unexpectedly. I have checked the system log at the time of the crash but there is nothing, hence long shot.

Anything likely to be crashing the machine? I have a suspicion its the updater as its crashed not long after the message comes up saying that there are updates available.

It usually happens a couple of times then after a forced reboot the system will stay up for hours without a problem. It's started to really annoy me and I really dont want to go back to Windows 

Any ideas, help etc would really be appreciated.

---

### Post by Shatrat on 2006-12-15
My first suspect would generally be the video drivers, especially since there was a kernel update recently.  
You might want to go back and reinstall the video drivers so that any mismatch with the kernel that may exist is fixed.

---

### Post by mells on 2006-12-15
great stuff, I'll try that. 

I haven't actually installed the new kernel yet, as it's crashed on numerous attempts at updating the system.

---

### Post by Shatrat on 2006-12-15
> it's crashed on numerous attempts at updating the system.
In that case my usual prejudice against binary drivers might be misplaced.
You said you checked the log, which log?  Did you look for errors in dmesg and poke around in /var/log files for error messages?

---

### Post by PurplePenguin on 2006-12-15
My first instinct was video drivers, too... always give me problems. :)

---

### Post by mells on 2006-12-15
> **Shatrat said:**
> In that case my usual prejudice against binary drivers might be misplaced.
You said you checked the log, which log?  Did you look for errors in dmesg and poke around in /var/log files for error messages?

nope, the only system log I've checked is:

System > Admin > System Log

Will have a look at /var/log now.

---

### Post by mells on 2007-10-06
does anyone want to talk me through how to check the various logs again?

please... Its crashing again... Dont want to go back to windows :confused:

---

### Post by MarkieB on 2007-10-06
Not sure how to interpret them all, although to write all data to one file

insert into /etc/syslog.conf

"*.*  -/var/log/all"

the file creates itself

---

### Post by ddrichardson on 2007-10-06
> **mells said:**
> However, for the past few days I have had system crashes without warning. Nothing running at all, but as the system comes up it will just hang unexpectedly.

Before chasing one's tail, boot the live cd and run a memory test.

---

