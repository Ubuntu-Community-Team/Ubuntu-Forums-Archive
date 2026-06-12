---
title: "Recover Windows key from Ubuntu partition?"
date: 2013-07-03
forum: Any Other OS
---

### Post by Jaraxle on 2013-07-03
Does anyone knows of a way to recover a Windows 7 product key from a non-booting Windows partition? I had this problem earlier today on a dual-boot PC and could not find software that ran within Ubuntu. I was able to eventually find a utility, but only because I had a working Windows partition on a laptop. After installing this software in Windows 7 on my laptop, I was able to use the application to create a boot disk to use on the problem computer and was able to recover the key but it seems like there must be a way to do this from within Ubuntu.

Are there any scripts that run in Ubuntu that are able to recover the key from the registry on a Windows partition? How about recovering Windows user passwords? I know of a bootable disk that can recover account passwords but what I'm looking for is something that will run within Ubuntu on a dual-boot/multi-boot machine and extract the information on another partition. I intend to research this further but thought that someone would know off hand. Thanks.

---

### Post by mips on 2013-07-03
I dunno of a linux app that can do this but you can always copy the [COLOR=#333333][FONT=monospace]C:\Windows\System32\config [/FONT][/COLOR]folder and get the key using something like ProduKey from Nirsoft on another windows system.

If you know where in the registry to find the key you might be able to use one of the linux registry tools to extract it but I'm just taking a shot in the dark here, [http://www.forensicswiki.org/wiki/Windows_Registry](http://www.forensicswiki.org/wiki/Windows_Registry)

---

### Post by varunendra on 2013-07-03
> **Jaraxle said:**
> Does anyone knows of a way to recover a Windows 7 product key from a non-booting Windows partition?
[s]There seems to be a module "**libparse-win32registry-perl**" in the repository that seems to be dedicated to exactly what you want above -
> Parse::Win32Registry is a module for parsing Windows Registry files, allowing
you to read the keys and values of a registry file without going through the
Windows API.
I'm not sure about how to use it though.[/s] *[COLOR="#800000"](edit : forget it, I misunderstood it seems)[/COLOR]*
I do know that "**HBCD**" (Hiren's Boot CD) contains some ready to use tools to do that.

> **Jaraxle said:**
> How about recovering Windows user passwords?
There are plenty of tools to 'remove' the password immediately, "**chntpw**" being one of them which is available in Ubuntu repositories. However, there is only one program I know of that is able to actually "recover" user passwords - "**ophcrack**" - which is also available in the repos, but you'll have to manually get the rainbow tables that it works with. A better option is to just download the free ophcrack live cd that is pre-configured to automatically start doing this as soon as booted. For long and complex passwords, you'll need to purchase the advanced rainbow tables as required.

---

### Post by Jaraxle on 2013-07-03
I never thought about copying the C:\Windows\System32\config folder. That's a good idea. And I had never heard of chntpw. I have Ophcrack and HBCD but chntpw is the kind of tool I'm looking for. Thanks.

---

