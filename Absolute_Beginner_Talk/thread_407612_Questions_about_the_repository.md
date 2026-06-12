---
title: "Questions about the repository"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by chunho on 2007-04-12
I've just changed to using Ubuntu and have a question.

How can I know whether a software will be in the official repository or not? I think I've heard from somewhere that installing the software in the repository is better.However will there be software that will never be added into the repository?

For example Google Earth. I know that it is a commercial product so there may be chances that it will never be added to the repository. Therefore should I wait for it to be added or just download the one on the google website?

Another case is TripleA, which is a game. It is GPL so I thought it would be in the repository. But it isn't. Is there a reason?

Sorry for my clumsy English. Any help will be appreciated.

---

### Post by Sef on 2007-04-12
> How can I know whether a software will be in the official repository or not? I think I've heard from somewhere that installing the software in the repository is better.However will there be software that will never be added into the repository?

```
sudo aptitude search program_name
``` to search if a program is in the repositories.  

Also [universe and multiverse]("https://help.ubuntu.com/community/Repositories/Ubuntu") are not open by default.

---

### Post by chunho on 2007-04-12
Sorry if I'm not clear. What I really mean is that: Is there a general guideline as to what software would be added to the repository and what would never be?

Thanks.

---

### Post by zvacet on 2007-04-13
I think that is not possible to add all softwares we want to the repositories,so we search web trying to find deb package of wanted software or source code and compile it.

---

### Post by eentonig on 2007-04-13
In the standard repositories, you will only find software that has been tested and approved by the distrubtions maintainers.

This is as close as you can get to a 'Official certificate that this thing will work on your system and is garantueed virus/malware free'

The extra community repositories that you can enable offer a similar comfort, but to a more or less limited extent. Either because they are not verified by 'official' distro maintainers but by community members. Or because they are not available with source code (so we can't see the inner works of it).

And then you're always free to add extra and exotic repo's at your discretion. But, with no garantuees what so ever.

Someone correct me if I'm wrong.

---

### Post by chunho on 2007-04-14
Thank you very much.

---

