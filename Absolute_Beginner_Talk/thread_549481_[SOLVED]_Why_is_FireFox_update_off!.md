---
title: "[SOLVED] Why is FireFox update off?!"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by lordfkiller on 2007-09-12
Hello.

I just noticed that Firefox automatic update is off and cannot be turned on.
Why?
Why is the version of Thunderbird etc old in package managers?
Why do I have to use ubuntuzilla to update Mozilla products? Is it the same for all softwares?

Thanks.

---

### Post by kellemes on 2007-09-12
I guess Ubuntu doesn't want mozilla to update itself bypassing Ubuntu's magical world of package-management.

---

### Post by nanotube on 2007-09-12
> **lordfkiller said:**
> Hello.

I just noticed that Firefox automatic update is off and cannot be turned on.
Why?
Why is the version of Thunderbird etc old in package managers?
Why do I have to use ubuntuzilla to update Mozilla products? Is it the same for all softwares?

Thanks.

the autoupdate is off because you're /supposed/ to use the repos to update...

see my latest response to you in [http://ubuntuforums.org/showthread.php?t=549119](http://ubuntuforums.org/showthread.php?t=549119) about your other questions. :)

also, you don't /have/ to use ubuntuzilla - you can also install manually, or add a third-party repository (the iuculano repository is a frequently-used one, for thunderbird).

---

### Post by philinux on 2007-09-12
[COLOR=Black]the autoupdate is off because you're /supposed/ to use the repos to update...

definitely not.

just got to  [http://ubuntuzilla.wiki.sourceforge.net](http://ubuntuzilla.wiki.sourceforge.net)

and follow the procedure.[/COLOR]

---

### Post by lordfkiller on 2007-09-13
Is it correct that repos release updates some weeks after Mozilla? If yes, why?
I still do not understand why softwares in package managers are old.

---

### Post by philinux on 2007-09-13
[SIZE=2][COLOR=Black]Like it says in ubuntuzilla

[/COLOR][/SIZE]> [B][SIZE=2][COLOR=Black]Background 
The official repositories for a particular version of Ubuntu are composed to contain the latest versions of software packages as of the date of release of that version of Ubuntu. After the release is made, newer versions of software packages do not get added to the repositories, with the exception of security fixes. So, for example, the latest version of Thunderbird during Ubuntu 7.04 (Feisty) release was 1.5, so the repositories will contain 1.5, even though Thunderbird 2 was released afterwards. Furthermore, even the security patches are usually several days to a week or more behind the official Mozilla releases, due to the time it takes to test and package the software.[/COLOR][/SIZE][/B]

---

### Post by mcduck on 2007-09-13
> **lordfkiller said:**
> Is it correct that repos release updates some weeks after Mozilla? If yes, why?
I still do not understand why softwares in package managers are old.

Because all software updates are tested before loading into Ubuntu's repositories. Anyway, for important security updates it's more like day or two, not weeks.

---

### Post by stchman on 2007-09-13
> **lordfkiller said:**
> Is it correct that repos release updates some weeks after Mozilla? If yes, why?
I still do not understand why softwares in package managers are old.

Ubuntu is really good about updating Firefox.

---

