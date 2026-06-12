---
title: "Run PHP script from Command Line?"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by Rainmaker_mail on 2006-09-07
Dear All,
I have migrated my MediaWiki to Ubuntu6.06 LAMP Server edition.
After migration, all the images are gone and the help file mentioned i have to run a php script from command line, rebuildImages.php.

Unfortunately, i don't have php or php5 in my /usr/bin. How do i run the PHP script from CLI? I obviously can run from browser since i am able to install mediawiki 1.7.1 but have no idea how to on CLI

Btw, i check my php5 installation and its okay (from the php.info)
Rgds,
Jon

---

### Post by Uluen on 2006-09-07
Maybe [this]("http://www.google.no/search?q=How+do+i+run+the+PHP+script+from+CLI&start=0&ie=utf-8&oe=utf-8&client=firefox&rls=org.mozilla:en-US:unofficial") will help ;)

---

### Post by Rainmaker_mail on 2006-09-07
Dear Uluen,
Thank you for the suggestion. I should have tried that! in the first place.

Anyway, for those wanting to know - you will need to install an additional package, php5-cli. Once install you can run the script via CLI using php <scriptname>

Thanks,
RM

---

