---
title: "Trying to install iSight webcam; “module bcd_pci” not found - Google no help"
date: 2020-04-26
forum: Apple Hardware Users
---

### Post by dessertlizard on 2020-04-26
[COLOR=#242729][FONT=Arial]I'm a recently convert to Linux.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Running Ubuntu 19.04 on an older Macbook 4.1 or 4.4, white model, September 2008.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]It has an iSight camera which is the only thing that didn't work out of the box.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I'm following the instructions at:
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][https://askubuntu.com/questions/990218/camera-not-working-on-macbook-pro](https://askubuntu.com/questions/990218/camera-not-working-on-macbook-pro)
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Everything seems to work fine till the "**sudo modprobe -r bcd-pci**".
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Then I get a "**modprobe: FATAL: Module bcd_pci not found**".
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Google doesn't help and I can't find an explanation on the forums as to why this is happening. I can't get back to using OSX too. This system is limited to 10.7 and things are starting to get outdated/having compatibility issues especially online.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I'm aware my question might be tremendously simple to solve, but I'm really at a loss.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Yeah, I should just buy a new computer and get on with it. Unfortunaly, can't spend that much right now.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I'd be very thankfull if anyone could chime in.[/FONT][/COLOR]

---

### Post by howefield on 2020-04-26
Moved to the "Apple Hardware Users" forum.

---

### Post by CelticWarrior on 2020-04-26
Welcome.

First of all, Ubuntu 19.04 is out of support. There's no point in troubleshooting.
Please install the current Ubuntu 20.04. Then, if it doesn't work out-of-the-box, try the same instructions.

---

### Post by dessertlizard on 2020-06-06
Since the forums weren't that helpful and just reverted to the default *you must update* holy grail answers, which is sadly rather common I must say, I kept looking for a solution.

It's sort of working right now. I say sort of, because it works normally with programs that are made to use the webcam but has some issues being undetected in some browsers. That clearly has something to do with the browsers themselves and I'm still looking into it. So if you're faced with the same issues, you'll have to try a different browser that works for you.

Apparently there's a tool to help with this process. Some of the tutorials out there over complicate things a lot more than needed for the Linux newbie.

For a simplified install that works you should run "sudo apt-get install isight-firmware-tools".

Then the tool will ask you for the firmware file, in my case for a Macbook 4.1/4.4 I used [this]("https://www.linux.org/attachments/appleusbvideosupport-zip.4683/"). You should check if that one is suitable for your Apple laptop webcam.

If and when I have updates about the webcam not being detected by some browsers, I'll drop by and update the thread. This behavior happens either on 19.4 as well on 20.04 Ubuntu. Just so the possibility of it being the older OS version causing the issues can be excluded.
 [COLOR=#242729][FONT=Consolas]
[/FONT][/COLOR]

---

### Post by ajgreeny on 2020-06-06
> **dessertlizard said:**
> Since the forums weren't that helpful and just reverted to the default *you must update* holy grail answers, which is sadly rather common I must say, I kept looking for a solution.
The reason you get those comments is because it is just about impossible for us to help you as all the repos for 19.04 are unavailable and it's impossible to upgrade any packages on an EOL version of Ubuntu.

I am pleased you managed to figure out the answer to you webcam problem but that does not stop me also advising you very strongly to upgrade to a fully supported version.

---

### Post by dessertlizard on 2020-06-06
> **ajgreeny said:**
> The reason you get those comments is because it is just about impossible for us to help you as all the repos for 19.04 are unavailable and it's impossible to upgrade any packages on an EOL version of Ubuntu.

I am pleased you managed to figure out the answer to you webcam problem but that does not stop me also advising you very strongly to upgrade to a fully supported version.

I'm already running 20.04. The issue manifested itself on either versions. At the time of my initial post, 20.04 had been out three days. I'd be inclined to say much information, as well as software, was still available for 19.04. Yet, I might be completely wrong since I don't have an in-depth Linux knowledge. Not trying to antagonize anyone, I completely understand what you're saying, however answers like those  always come off a bit like low-effort posts. Updating isn't always the much desired action that solves it all.

---

### Post by DuckHook on 2020-06-06
> **dessertlizard said:**
> &#8230;I'd be inclined to say much information, as well as software, was still available for 19.04. Yet, I might be completely wrong since I don't have an in-depth Linux knowledge.
Like ajgreeny, I'm glad you sorted it out. It is worth noting that, once a version reaches EoL, it gets shuffled off to the dustbin of Canonical's repos. Expert users can redirect their sources.list to these museum archives long enough to enable upgrading, but since they no longer get patches, upgrading is about all that this technique is good for.
> Not trying to antagonize anyone, I completely understand what you're saying, however answers like those  always come off a bit like low-effort posts. Updating isn't always the much desired action that solves it all.
Now that you are on a supported release, the issue has become academic, but for new users who may come across this thread, the reasons that the old-timers here give the response that we do are twofold:

[LIST=1]
[*]On a community level, it is irresponsible to enable the resurrection of zombie versions. The Windows world is infested with malware in large part because millions still run obsolete systems going as far back as XP. A huge number of these machines have been subverted into the massive bot network that scumbags use to attack the rest of us. This dynamic exists only because of an insistence on old OSes that amounts to nothing less than wilful negligence.
[*]From a pragmatic perspective, it is not possible to help those who insist on necromancing undead versions. The geeks that run Linux are heavily invested in running secure systems, which means that few, if any, still have dead versions installed. This means that we no longer have a test&#8209;bed on which to reproduce issues even if we wanted to.
[/LIST]
Though the standard answer to running unpatchable versions may seem abrupt and high&#8209;handed, it is the most "helpful" reply possible, provided that the objective is OS health and security hygiene. What's truly ***un***helpful is compromising the larger Linux ecosystem by insisting on dead operating systems that are nothing more than open invitations to getting oneself pwned.

---

