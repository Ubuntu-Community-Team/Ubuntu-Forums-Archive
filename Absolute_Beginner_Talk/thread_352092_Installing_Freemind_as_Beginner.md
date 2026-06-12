---
title: "Installing Freemind as Beginner"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by P235 on 2007-02-02
Greetings, I have taken some time to read over the details as to how to install Freemind, but for certainty I simply wish to bring up this matter once more for my own sake.  I am using Ubuntu 6.10.

According to the instructions provided by the (link)[siliconchaos]("http://siliconchaos.blogspot.com/2006/05/setting-up-freemind-in-ubuntu-dapper.html")(/link) blog, one would require libcommons-lang-java and librelaxng-datatype-java before installing libforms-java_1.0.5-2_all.deb.  But, according to the (link)[InstallingSoftware]("https://help.ubuntu.com/community/InstallingSoftware")(/link) page, gdebi should check the package's dependency requirements for you.  Can I simply use gdebi to install libforms-java_1.0.5-2_all.deb and the rest of Freemind, or should I continue to follow siliconchaos' instructions for Ubuntu Dapper?

---

### Post by greybirds on 2007-02-02
Have you tried using the repositories that Freemind has set up?

[http://sourceforge.net/project/shownotes.php?release_id=355162](http://sourceforge.net/project/shownotes.php?release_id=355162)

grey

---

### Post by P235 on 2007-02-02
Perhaps editing my sources is the easiest way to install Freemind, but I am uncomfortable with adding repos of unfamiliar groups.  Nonetheless, I did as you suggested and I have learned that siliconchaos' instructions remain relevant to Ubuntu 6.10 because librelaxng-datatype-java, libcommons-lang-java, libjgoodies-forms-java, and libcommons-codec-java are all required.

So, in the case of when one adds repos from SourceForge, is that source considered trustworthy?

---

