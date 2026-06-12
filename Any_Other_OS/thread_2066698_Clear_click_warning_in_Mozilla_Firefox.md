---
title: "Clear click warning in Mozilla Firefox"
date: 2012-10-05
forum: Any Other OS
---

### Post by rapattack1 on 2012-10-05
I am using Artistx which is based on Ubuntu and in Mozilla Firefox on this one website i am getting a Clear Click warning which i think comes from NoScript. I really don't know what to do with it. Its a legit website that i am voting on...wanting to vote on. This applet stops me from doing so. What do i do with this and what does it mean?
[http://www.brainartproject.com/entry/sam-fonte/#.UFxCXK7jr9c](http://www.brainartproject.com/entry/sam-fonte/#.UFxCXK7jr9c)

---

### Post by nothingspecial on 2012-10-05
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by mike acker on 2012-10-05
hidden clickables are a favorite attack vector -- which is why NOSCRIPT flags that

i have been reading reports on a new "Man in the Browser" (MITB) attack last couple days..... e.g. see [http://www.scmagazine.com.au/News/318058,new-web-attack-immediately-siphons-stolen-data.aspx](http://www.scmagazine.com.au/News/318058,new-web-attack-immediately-siphons-stolen-data.aspx)

if you read these they all depend on un-authorized modifications to the victim's computer. this is the reason I'm now a LINUX user.

I'm still chewing on this -- although the folks on this forum are a wonderful help!!

the crap that is thrown at us via our browsers is (e.g.) JavaScript -- or byte-code (e.g. C#, .NET ... PHP?? (not sure if PHP is byte code or script) ) is a major vector for these software attacks

the browser "interprets" the script or byte code, carrying out the instructions thus provided -- allowing the web page some control over our computer

"some control over our computer"

this is the Front Line of the Hacking War. How much can that web page do ?

XP computers were a push-over; Win7 with UAC is much better... as far as protecting the o/s is concerned. i don't think it protects the browser from -- what i'll just call "attached instructions" --

this article was a real eye-opener for me:
[http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/](http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/)

it's a little dated but very insightful,-- particularly the discussion of USERLAND and the remote procedure call (RPC) mechanism used in windows

_The Rootkit Arsenal_ Bill Blunden ISBN-13: 978-1-59822-061-2 contains detailed explanations of memory protection -- which -- if i read it right -- windows only partially implements the memory protection model, choosing instead to rely on the virtual memory management mechanism...

now as we start getting around these concepts what we start looking for is "mouseholes" -- data paths available to the hacker through which he can deliver "malware" -- un-authorized changes to a remote computer.

I don't think they can get at your browser program *per se* in Linux.  the question will be then : can they deposit any "special instructions" that your browser will pick up automatically when you load it ?

this sort of stuff could only be dropped in the user libraries associated with the logged on account

my thinking then is: I will use a separate LOGON for General Surfing and another separate log on for any critical activity e.g. shopping at NewEgg, Amazon, -- anything that deals with money or other sensitive personal information

I was involved in computer programming when we switched people from 1401 to System/360.  This is the transition from a monolithic system ( like a 1401 or a 5150 type PC ) to a multi-user system -- like Linux or System/370

It is my belief we do not need to suffer from all this hacking,-- if we just make security a priority instead of ease of use and the latest dizzle-dazzle.

---

### Post by critin on 2012-10-06
I would keep it locked and try another browser if voting is important to you.  The message sounds like a click hijacking (maybe to change your vote?)

I opened the link and found nothing wrong, but I didn't click on anything.  Clearing the browser cache may help, but if it's a real hijacking it probably won't delete it.

---

### Post by rapattack1 on 2012-10-09
Thanks i used chrome. :0)

---

