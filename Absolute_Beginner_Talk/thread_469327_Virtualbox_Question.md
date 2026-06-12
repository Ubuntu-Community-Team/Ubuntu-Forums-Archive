---
title: "Virtualbox Question"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by teh'p3nsi0n3r on 2007-06-09
Hi, just a quick question, ive been searching the forums and google for an awnser, i final got windows xp setup within a virtualbox on my kubuntu desktop and its running great for applications etc, my question though is that two or three times now i have went away and left the virtualbox running to do something else and when i come back Virtualbox is still running but the virtual xp window has shutdown, I've not even got alot of other process's on the go, so i was thinking is it maybe a timer within virtualbox that closes the window when its idle for a certain period of time? or is there something im missing, it doesnt close when i am using it normally.

Thanks.

---

### Post by Bachstelze on 2007-06-09
I have experienced the same thing more than once. I just got back to vmware and I'm happy again :)

---

### Post by teh'p3nsi0n3r on 2007-06-09
Hi thanks for the quick response :KS 

is this something thats common/problem with virtualbox then? is there a way to fix this, or is it something ill just have to live with? :)

Thanks.

---

### Post by starcraft.man on 2007-06-09
Uh, I'm not sure I follow. What do you mean by "XP window shut down"? You mean the VM itself (the XP VM) has shut down spontaneously? Or you mean the window minimized to the task bar? I been using it for over a month now and can say I never got this issue... have you upgraded to 1.4?

---

### Post by teh'p3nsi0n3r on 2007-06-09
hi there,

sorry if i wasnt clear, yes i mean the vm xp windows closes itself (it is no longer open the tasks ends) by itself (its no longer in the task bar, although the virtualbox program that launches the vm windows is still present, although when i am using it i dont have this problem only seems to be when my laptop is idle, i am using 1.4.0 ubuntu deb for feisty from the virtualbox website.

Thanks.

---

### Post by HotShotDJ on 2007-06-09
I use VirtualBox (1.3.8 ) on Kubuntu 7.04 with Windows 2000 as the guest OS.  I've never had the problem you describe.

@starcraft.man -- Thanks for the heads-up on the VirtualBox update!  I'll be updating after work tonight. :)

---

### Post by teh'p3nsi0n3r on 2007-06-09
hmm strange then, its crashed (closed) twice today now, once about 10 minutes ago, hymntolife stated he/she had this problem also but switched back to vmware, so its obviously not just myself.
One thing i have noticed when looking back at the virtualbox launcher (main window) it would show the vm xp as "aborted" (where it usually says running) after it closes itself, 

Thanks.

---

### Post by starcraft.man on 2007-06-09
> **teh'p3nsi0n3r said:**
> hi there,

sorry if i wasnt clear, yes i mean the vm xp windows closes itself (it is no longer open the tasks ends) by itself (its no longer in the task bar, although the virtualbox program that launches the vm windows is still present, although when i am using it i dont have this problem only seems to be when my laptop is idle, i am using 1.4.0 ubuntu deb for feisty from the virtualbox website.

Thanks.

Ok now that is seriously weird. And this is the only program that spontaneously closes windows? I gotta think its something to do with your set up. I don't know enough though to tell you exactly what.

I'm gonna send ya to their [forums here]("http://forums.virtualbox.org/"). Plenty of knowledgeable folk there, give em your hardware spec and list any special programs you had running at the time.

The one thing that comes to my mind is that your labtop is doing something to power save after a while of you being gone (suspend function, or something similar...) and the VM can't handle being suspended (any interruption of its operation while its live will obviously result in it crashing) or otherwise stopped in its resources while its active. If thats the case you have to look at your power management options or such. Post on the forum anyway, I'm just guessing :).

> **HotShotDJ said:**
> I use VirtualBox (1.3.8 ) on Kubuntu 7.04 with Windows 2000 as the guest OS.  I've never had the problem you describe.

@starcraft.man -- Thanks for the heads-up on the VirtualBox update!  I'll be updating after work tonight. :)

Np, glad to be of help. It is a good upgrade, has lots of new features. Like bidirectional clipboard :D.

Edit: hehe almost forgot the link to forums :D.

---

### Post by teh'p3nsi0n3r on 2007-06-09
thanks for your help starcraft.man, ill look into it. :)

---

### Post by starcraft.man on 2007-06-09
> **teh'p3nsi0n3r said:**
> thanks for your help starcraft.man, ill look into it. :)

No problem. Thats what we here for. Have fun :D.

---

### Post by machoo02 on 2007-06-09
> **starcraft.man said:**
> The one thing that comes to my mind is that your labtop is doing something to power save after a while of you being gone (suspend function, or something similar...) and the VM can't handle being suspended (any interruption of its operation while its live will obviously result in it crashing) or otherwise stopped in its resources while its active. If thats the case you have to look at your power management options or such. Post on the forum anyway, I'm just guessing :).

Are you sure about this??  I'm *fairly* certain that I've been able to suspend/hibernate my laptop with a VM running without problem....

---

### Post by xxzeenoxx on 2007-06-23
I've experienced the same exact issue with the latest virtualbox, and on more than one occasion.  I was doing some simulations in multisim and the virtual session just closed completely, but the virtualbox manager remains open.

---

### Post by LGer on 2007-07-01
Me too. Aborts XP like it was shot out of a cannon. Any ideas?

Was running Civ II at the time. Does it all the time in there.  Thought maybe it was the auto-save. However.... I've also had it abort a few times when just browsing the web.

---

### Post by Gary.M on 2007-07-19
Has anyone found a fix for this? I am also seeing randon aborts. The VM just disappears. Can't seem to get any answer on the Virtualbox forum. Others are reporting this too.

---

### Post by teh'p3nsi0n3r on 2007-08-10
nope ive just managed to put up with the issue, its not been occuring as much as it was previously though, i did read the VB forums and can see same issues with others.

---

### Post by asmoore82 on 2007-08-10
A think we need to take an inventory of who's using Open-Source Edition and who's not.

I use OSE that I compiled myself and have no problems to report.

---

