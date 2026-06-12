---
title: "Binary Packages, Use At Your Own Risk!"
date: 2005-07-20
forum: Announcements &amp; News
---

### Post by jdong on 2005-07-20
Recently, we've seen many members of our community making binary .deb packages and posting them on the forums for others to use.

I'd like to trust that all our members have good intentions for doing so (I've yet to see otherwise), and haven't sneaked little nasties within the packages. However, there are potential quality issues with some of the packages posted. Some are "Backports"-style contributed packages without the "~" version trailer, which would make upgrading to Breezy unsuccessful or extremely painful. Others are just packages put together with the "checkinstall" tool, which are of a very low quality since they don't contain proper dependency information for reliable interaction with other packages.


**To those making packages**:

We commend your efforts, trying to make it easier for others to get the software they want. :) However, please exercise some extra courtesy: disclose how you made the package (debhelper+pbuilder, checkinstall, "Backports", alien, etc) and what kind of quality you think the package would be in, in relation to Debian/Ubuntu standards. Also, if you're making a package that supersedes a current Ubuntu package (i.e. "Backport"), utilize the "~" version operator to make sure upgrading will go smoothly later on.

**To those potential users:**

Exercise good judgement. Is the person posting the package trustworthy? Does he already have a good track record with these packages? Is he a Ubuntu, Debian, or Backports developer? These will help you make a better informed decision.



**Moderators reserve the right to remove attached packages or links to packages that they feel are NOT generally safe for users to use**.


Thanks,
UbuntuForums staff.

---

