---
title: "Firefox 19 on PowerPC"
date: 2013-02-25
forum: Apple Hardware Users
---

### Post by powerpcliberation on 2013-02-25
This is not a question but rather a calling to all PowerPC Ubuntu users to see if you're having the same Firefox 19 issues I am.

It works fine for me other than many images get a blueish tint over them.  Anyone else experiencing this?  Hopefully it will be fixed in 19.01.

For the record I have this same issue in both Lubuntu 12.04 and Lubuntu 13.04.

---

### Post by powerpcliberation on 2013-02-25
Just found a fix!

Go to about:config and change the following string from true to false by simply double clicking the line:  image.high_quality_downscaling.enabled

Now it renders all images perfectly.

A very quick and easy fix for all.

Found the fix here:
[http://www.mail-archive.com/desktop-packages@lists.launchpad.net/msg204246.html](http://www.mail-archive.com/desktop-packages@lists.launchpad.net/msg204246.html)

---

### Post by rsavage on 2013-02-25
Top of the list when you search firefox bugs for "blue" ordered by newest first. 
 
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bugs?field.searchtext=blue&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=OPINION&field.status%3Alist=INVALID&field.status%3Alist=WONTFIX&field.status%3Alist=EXPIRED&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.status%3Alist=FIXRELEASED&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&assignee_option=any&field.assignee=&field.bug_reporter=&field.bug_commenter=&field.subscriber=&field.tag=&field.tags_combinator=ANY&field.status_upstream-empty-marker=1&field.upstream_target=&field.has_cve.used=&field.omit_dupes.used=&field.omit_dupes=on&field.affects_me.used=&field.has_patch.used=&field.has_branches.used=&field.has_branches=on&field.has_no_branches.used=&field.has_no_branches=on&field.has_blueprints.used=&field.has_blueprints=on&field.has_no_blueprints.used=&field.has_no_blueprints=on#show_id=false&show_information_type=false&show_tag=false&show_reporter=false&show_targetname=false&show_assignee=false&show_date_last_updated=false&show_datecreated=false&show_importance=false&show_heat=false&show_milestone_name=false&show_status=false&batch_key=%5B%22-datecreated%22%2Cnull%2Ctrue%2C0%5D](https://bugs.launchpad.net/ubuntu/+source/firefox/+bugs?field.searchtext=blue&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=OPINION&field.status%3Alist=INVALID&field.status%3Alist=WONTFIX&field.status%3Alist=EXPIRED&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.status%3Alist=FIXRELEASED&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&assignee_option=any&field.assignee=&field.bug_reporter=&field.bug_commenter=&field.subscriber=&field.tag=&field.tags_combinator=ANY&field.status_upstream-empty-marker=1&field.upstream_target=&field.has_cve.used=&field.omit_dupes.used=&field.omit_dupes=on&field.affects_me.used=&field.has_patch.used=&field.has_branches.used=&field.has_branches=on&field.has_no_branches.used=&field.has_no_branches=on&field.has_blueprints.used=&field.has_blueprints=on&field.has_no_blueprints.used=&field.has_no_blueprints=on#show_id=false&show_information_type=false&show_tag=false&show_reporter=false&show_targetname=false&show_assignee=false&show_date_last_updated=false&show_datecreated=false&show_importance=false&show_heat=false&show_milestone_name=false&show_status=false&batch_key=%5B%22-datecreated%22%2Cnull%2Ctrue%2C0%5D)

---

### Post by powerpcliberation on 2013-02-25
> **rsavage said:**
> Top of the list when you search firefox bugs for "blue" ordered by newest first. 
 
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bugs?field.searchtext=blue&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=OPINION&field.status%3Alist=INVALID&field.status%3Alist=WONTFIX&field.status%3Alist=EXPIRED&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.status%3Alist=FIXRELEASED&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&assignee_option=any&field.assignee=&field.bug_reporter=&field.bug_commenter=&field.subscriber=&field.tag=&field.tags_combinator=ANY&field.status_upstream-empty-marker=1&field.upstream_target=&field.has_cve.used=&field.omit_dupes.used=&field.omit_dupes=on&field.affects_me.used=&field.has_patch.used=&field.has_branches.used=&field.has_branches=on&field.has_no_branches.used=&field.has_no_branches=on&field.has_blueprints.used=&field.has_blueprints=on&field.has_no_blueprints.used=&field.has_no_blueprints=on#show_id=false&show_information_type=false&show_tag=false&show_reporter=false&show_targetname=false&show_assignee=false&show_date_last_updated=false&show_datecreated=false&show_importance=false&show_heat=false&show_milestone_name=false&show_status=false&batch_key=%5B%22-datecreated%22%2Cnull%2Ctrue%2C0%5D](https://bugs.launchpad.net/ubuntu/+source/firefox/+bugs?field.searchtext=blue&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=OPINION&field.status%3Alist=INVALID&field.status%3Alist=WONTFIX&field.status%3Alist=EXPIRED&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.status%3Alist=FIXRELEASED&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&assignee_option=any&field.assignee=&field.bug_reporter=&field.bug_commenter=&field.subscriber=&field.tag=&field.tags_combinator=ANY&field.status_upstream-empty-marker=1&field.upstream_target=&field.has_cve.used=&field.omit_dupes.used=&field.omit_dupes=on&field.affects_me.used=&field.has_patch.used=&field.has_branches.used=&field.has_branches=on&field.has_no_branches.used=&field.has_no_branches=on&field.has_blueprints.used=&field.has_blueprints=on&field.has_no_blueprints.used=&field.has_no_blueprints=on#show_id=false&show_information_type=false&show_tag=false&show_reporter=false&show_targetname=false&show_assignee=false&show_date_last_updated=false&show_datecreated=false&show_importance=false&show_heat=false&show_milestone_name=false&show_status=false&batch_key=%5B%22-datecreated%22%2Cnull%2Ctrue%2C0%5D)

Thanks but that contains all the same info that I linked to.  Simply a different page.  Granted that your link is an official bug page.

---

### Post by rsavage on 2013-02-26
> **powerpcliberation said:**
>  Granted that your link is an official bug page.
My point was that you should of looked there first. If you don't find your bug then raise it. If you do find your bug then confirm it (click the affects me button). The more people that make a fuss (the more 'heat' it has) the more chance it has of being fixed. In my case I knew that it could of been raised too on mozilla bugs so I searched there too and linked the bug I found to launchpad. That is the workaround you found. PowerPC users have to be more proactive and actually look for solutions and report them to packagers.

---

### Post by powerpcliberation on 2013-02-26
> **rsavage said:**
> My point was that you should of looked there first. If you don't find your bug then raise it. If you do find your bug then confirm it (click the affects me button). The more people that make a fuss (the more 'heat' it has) the more chance it has of being fixed. In my case I knew that it could of been raised too on mozilla bugs so I searched there too and linked the bug I found to launchpad. That is the workaround you found. PowerPC users have to be more proactive and actually look for solutions and report them to packagers.

You're 100% correct.

That is the avenue I would normally take in say the BSD world but I am still a bit of a Linux novice in terms of instincts of where to go for tested fixes.  I am a BSD user since the 80's and I also develop for OpenBSD based clusters now but it has only been since around Aug. 2012 that I have really started using Linux and only really in my spare time.

I have a preference for PowerPC hardware because of it's incredible reliability (esp. G4 towers) and I wanted to start learning more Linux to help keep the architecture alive.  The reality is that an OS like Lubuntu PowerPC is the best option in my opinion for the average user to rejuvenate their older macs with modern secure software.  BSD is a bit much to grasp for the typical user coming from Mac OS so Linux is the best OS to push for the platform all round.

Once I have more time I would like to bring my BSD development skills to PowerPC Linux to see how I can contribute.  I simply need more time and a better idea of exactly what area of need my abilities can compliment the best.

---

### Post by barbaGNU on 2013-02-27
good catch, thanks for the tip!
 
Nel

---

