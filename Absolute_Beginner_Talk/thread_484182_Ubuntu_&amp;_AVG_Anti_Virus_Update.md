---
title: "Ubuntu &amp; AVG Anti Virus Update"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by TheXO on 2007-06-25
Dear All,

Just thought I'd share my recent experience with everyone here and hope it may provide someone with help in the future.

It regards AVG Anti Virus installed on Ubuntu Fiesty Fawn and the update procedure.  I was having trouble getting the update to run, so my definitions were out of date.  Each time I attempted an update I was told I had insufficient permissions.

Anyway, after a little research I found out that the current logged on user must be part of the AVG "group" created upon install.  To do this;

System -> Administration -> Users & Groups
Then click "manage groups"
Scroll to the "avg" group
Click "properties"
Add the relevant users to that group
REBOOT

The run the update and it should work!  Happy scanning :-)

---

### Post by pavpan on 2007-06-25
There is no need to reboot. All you have to do is log out and log back in. (System > Exit > Log Out)

I don't see why you have a virus scanner though. There's something like a grand total of 14 viruses for linux.

[Wikipedia: List of Linux Computer Viruses]("http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses")

---

### Post by cogadh on 2007-06-25
Yeah, and all of them are now patched so they are no longer a threat.

---

### Post by TheXO on 2007-06-25
Well, a reboot cured it for sure - just to be on the safe side (old windoze habits die hard :-p lol)

I know, but lets not be complacent... that leads to a massive disaster.  Just because there are no viruses, doesn't mean there never will be.  I know Linux is far far superior to windoze in many ways, but it never hurts to be prepared.

Good hunting!

---

### Post by FleetAdmiral74 on 2007-06-25
> **cogadh said:**
> Yeah, and all of them are now patched so they are no longer a threat.

The main reason for virus detection on Linux is for Windows files. For example, even though Linux is not vulnerable to many Windows viruses, if it handles them in email or docs, it can still spread them, so its more for *others* protection.

---

### Post by TheXO on 2007-06-26
I take it there is also little/no spyware on Linux either?  Excluding cookies and the like, I'm talking about malware specifically.

---

### Post by cogadh on 2007-06-26
Nope, not really. Unlike Windows, flaws in Linux that would allow malware and viruses to proliferate are patched too quickly for the malware writers to take advantage of. 

If someone discovers a flaw in Windows, MS can takes months to develop and test a patch. They also won't tell their users about the flaw until the patch is ready. Meanwhile, innocent Windows users are continuing to spread malware infections between each other, all because MS didn't bother to give them the "heads up" about the problem.

With Linux, on the other hand, if a flaw is discovered, a call goes out to the entire Linux community and you can sometimes have a functional patch within 24 hours. Even if a patch isn't available quickly, the information on the flaw is shared with everyone, with advice on how you can protect yourself until a patch is available.

Added to that is the fact that Linux is only used on less than 5% of the 650,000,000 PCs worldwide, while Windows is used on just about 95% of them, and Linux becomes a not too desirable target for the malware writers.

---

### Post by jso2897 on 2007-06-26
And that, my friend, is why some of us get virus protection for our Linux boxes. Like some others above, I swap files back & forth betwixt Win and Lin machines. Anyway, I was just curious, so i downloaded and installed AVG Free. On my machine, at least, all the fancy instructions they supplied (in an IMMENSE PDF file) proved unnecessary - I just clicked on the deb package and it installed and worked from the App menu right out of the box.
As a side note, somebody gave me an explanation of Adware on Linux?FF machines - according to him, you can pick up spyware & tracking cookies, and they will even function, reporting back to their target sites - but they can't install themselves marked for un-deletion, so when you do an ordinary cache cleanout on your browser, and delete your cookies, any adware is deleted like any regular cookie would be in Windows. It makes sense to me, but I don't know if it's entirely correct.

---

### Post by cogadh on 2007-06-26
Tracking cookies have both good and bad uses and they are common to both Windows and Linux. If you are reasonably security aware, they are not a real problem on either platform. As for spyware, there isn't any on Linux, there has never been any that can run on Linux, but that doesn't mean there never will be.

---

### Post by jmax on 2007-11-19
ani virus programs for linux are needed not for linux users but for
windows users who might get infected via a linux email ... well, I'm
no expert ... the way I updated my avg in linux tho is just get a 
root terminal up and put in "avggui" and just click on the update
button ... tis all that's needed ... at least on my machine.

---

### Post by bill_greene on 2008-01-13
> **TheXO said:**
> Dear All,

Just thought I'd share my recent experience with everyone here and hope it may provide someone with help in the future.

It regards AVG Anti Virus installed on Ubuntu Fiesty Fawn and the update procedure.  I was having trouble getting the update to run, so my definitions were out of date.  Each time I attempted an update I was told I had insufficient permissions.

Anyway, after a little research I found out that the current logged on user must be part of the AVG "group" created upon install.  To do this;

System -> Administration -> Users & Groups
Then click "manage groups"
Scroll to the "avg" group
Click "properties"
Add the relevant users to that group
REBOOT

The run the update and it should work!  Happy scanning :-)

[COLOR="Navy"]Tried your suggestion and it did not work for me. I have to "sudo avggui" then update from there.[/COLOR]

---

### Post by Pizarro on 2008-02-11
Got a similar problem since upgrade to 7.10. can run the downloads (sudo avgupdate -o   or sudo avggui) they download then..................avggui: /opt/grisoft/avggui/prog/messagebox.py:25: ERROR: Online update failed.
Reason: Error occurred while processing the update files.

---

