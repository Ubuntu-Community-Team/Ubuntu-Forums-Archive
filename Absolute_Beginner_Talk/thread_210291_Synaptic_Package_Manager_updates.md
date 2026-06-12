---
title: "Synaptic Package Manager updates"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by FuzZy2006 on 2006-07-06
Why do updates come so late? Gaim 2.0 came up and Synaptic has 1.2. The same is with java plugin, amarok, mplayer and many others ](*,)

---

### Post by Jagot on 2006-07-06
The Ubuntu repo's have 1.5 - which is the latest stable version - Gaim 2.0 has not been released yet - it's still only beta 3 which is why it won't be in the repositories.

Ubuntu's repositories are never far behind if at all, but sometimes it can take a little while for them to add an updated package to repo's so as that testing can occurr to ensure the updated packages don't affect anything else.

---

### Post by FredB on 2006-07-06
Why being so hungry of bleeding edge version. Do you need the latest version for both ? Is there any feature you absolutely need ?

Ask yourself this before anything else.

---

### Post by Jucato on 2006-07-06
Well, sometimes newer versions have bug fixes or security patches, like Firefox. 
The reasons why Ubuntu (not just Synaptic) does not add a new  version immediately are:

1. The new version was released after the feature freeze in the development process. Feature freeze is a stage in the development process where you don't add any new features/releases/programs to the distro in order to maintain stability.

2. The new version was released after Dapper was released. In this case, the one responsible for maintaining that program has to make an update. But before he could do that, he has to test the newest version to make sure that it doesn't cause any conflict with the rest of the system. After that, he has to package that program in a way that would not damage your already stable system. That the reason for the delay in providing updates to new versions. (Security updates have a higher priority, so it arrives faster)

3. The newer versions require newer libraries/packages that the current Ubuntu version does not yet support, and installing new libraries will break the dependencies of other packages. In this case, it's highly unlikely that an update will be provided, unless it's a very important (meaning critical) piece of software.

Maintaining system stability and at the same time providing up-to-date packages is not a very easy task. There are delays because developers/maintainers need to make sure that the newest and latest doesn't destroy your best system. 

Hope that helps.

---

