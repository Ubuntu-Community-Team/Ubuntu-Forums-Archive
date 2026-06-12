---
title: "php4"
date: 2007-04-20
forum: Apple PPC Users
---

### Post by kingmoffa on 2007-04-20
Hi all  , 

I've just used the live cd and am considering installing. One little point, I need php4 but it isn't available in synaptic using the default repos that feisty comes with. 

Could anyone pls point me in the right direction?

Thanks in advance.

---

### Post by grazie on 2007-04-20
php4 support was dropped from feisty. You'll need to go to edgy (6.10) or earlier if you want an Ubuntu supported php4 package.

---

### Post by kingmoffa on 2007-04-23
Had a feeling it might have been. Thanks for the help anyway. Looks like its a compile from source or look for some 3rd party repo that will work.

At least red hat have kept support , my servers are safe.

---

### Post by siennalizard on 2007-04-26
You might be interested in my article [http://jdv.hopto.org/index.php?/archives/84-Ubuntu-Feisty-with-Apache-2.2,-PHP4-with-FastCGI-and-MySQL-support.html](http://jdv.hopto.org/index.php?/archives/84-Ubuntu-Feisty-with-Apache-2.2,-PHP4-with-FastCGI-and-MySQL-support.html) which explains how I got PHP4 to work on Feisty without breaking the PHP5 implementation too much. YMMV, but it works for me. Comments would be appreciated.

---

### Post by Bat on 2007-05-10
Yet another stupid decision on the part of the Ubuntu maintainers.  When are they going to learn?  **PHP 5 failed.  The only worthwhile version of PHP is PHP 4.**  Why?  Because PHP is installed on web hosts, and web hosts have to support multiple customers, and customers see no reason to upgrade a system that's "good enough", which PHP 4 is (just barely).  So the web hosts don't upgrade, so PHP 5 is useless for anyone who doesn't host their own sites.  And since hosting your own sites is a mug's game if you want to have reasonable up-time, the circle closes and the story ends.  Add to this the fact that PHP's maintainers can't even manage to avoid breaking valid code with their minor point releases, and why would you upgrade to version 5 at all?  So that your object-oriented code can be on par with C++ in the 1980s?  Big deal!  It's not like the script kiddies who produce 99% of PHP code ever use classes and objects!  Or... how about because you want all the libraries and third-party add-ons to suddenly break with no option to replace them?  Yeah, that'd be fun.

Ubuntu needs PHP 4, because we live on the planet Earth, where reality trumps ideology.  Will someone please get a clue and fix this?

---

### Post by Nathaniel on 2007-05-24
I second that, actually. PHP4 is still a major player, obsolete or not. I can't easily do my job simply because I can't set up my workstation to use the same modules as the server. I'm struggling with XSLT support, which seems to have been completely switched about between PHP4 and 5.

People still ride trains, don't they? They can't turn, nor do much but go forward, and in comparison to busses and planes they're pretty much obsolete. Yet people ride them every day. PHP4 is the trusty old train that simply just gets you to where you need to go. And when there aren't even any roads to get there, only train tracks, I find it mildly annoying when people call my train obsolete.

People still need PHP4, simple as that. We shouldn't have to be stuck in older distributions simply because PHP5 exists.

---

### Post by chrisUK1 on 2007-06-06
> **Bat said:**
> Yet another stupid decision on the part of the Ubuntu maintainers.  When are they going to learn?  **PHP 5 failed.  The only worthwhile version of PHP is PHP 4.**  Why?  Because PHP is installed on web hosts, and web hosts have to support multiple customers, and customers see no reason to upgrade a system that's "good enough", which PHP 4 is (just barely).  So the web hosts don't upgrade, so PHP 5 is useless for anyone who doesn't host their own sites.  And since hosting your own sites is a mug's game if you want to have reasonable up-time, the circle closes and the story ends.  Add to this the fact that PHP's maintainers can't even manage to avoid breaking valid code with their minor point releases, and why would you upgrade to version 5 at all?  So that your object-oriented code can be on par with C++ in the 1980s?  Big deal!  It's not like the script kiddies who produce 99% of PHP code ever use classes and objects!  Or... how about because you want all the libraries and third-party add-ons to suddenly break with no option to replace them?  Yeah, that'd be fun.

Ubuntu needs PHP 4, because we live on the planet Earth, where reality trumps ideology.  Will someone please get a clue and fix this?

PHP5 failed? When was that? Must have missed that one. My hosting company has used PHP5 from word go. Since I develop XML/PHP powered sites I'm greatful for them for having the forsight to upgrade. PHP4 is good, and I daresay it probably suits the majority of PHP scripters, but for corporate infrastructure PHP5 is the way to go.

I cant say I appluad Ubuntu for dropping PHP4 but it is one of the reasons i finally kicked OSX.

Just my 2 pence worth

---

### Post by stmiller on 2007-06-06
Yeah ubuntu makes all kinds of illogical political decisions. They should leave ALL options and choices on the table. If other distros figured out how to do it, it should be possible.

---

### Post by pestilence on 2007-06-09
[http://pestilence.insert.gr/ubuntu-feisty-704-and-php4-howto/](http://pestilence.insert.gr/ubuntu-feisty-704-and-php4-howto/)
Enjoy! :)

---

