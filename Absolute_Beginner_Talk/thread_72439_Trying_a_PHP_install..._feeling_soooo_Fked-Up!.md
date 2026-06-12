---
title: "Trying a PHP install... feeling soooo F*ked-Up!"
date: 2005-10-06
forum: Absolute Beginner Talk
---

### Post by Lord Brar on 2005-10-06
Well... I must have read through every help file out here and I am trying to figure out how to install php.

I know I can do it using package manager but for that I'd need net connection which I have failed to setup on ubuntu (ADSL... Ubuntu can't recognize access concentrator when I type in sudo pppoeconf). :(

I either need a way to setup my internet on linux or I need some way to install php (I need it as a test server. On a sidenote, I installed mysql and apache on the computer manually but when building php it says a lack of lex and bison alsong with some other packages).

Here's an Idea : Can anyone tell me how to find what all packages are required to install php that I am missing and how to create a repository with the cd of those missing components (which I can download from the archive site)?


I'd really appreciate it. Thanks :)

---

### Post by KingBahamut on 2005-10-06
[http://packages.ubuntu.com](http://packages.ubuntu.com)

You should be able to find all of php and its deps in there. 

To make a repo CD.

---

### Post by Lord Brar on 2005-10-06
[QUOTE=KingBahamut][http://packages.ubuntu.com](http://packages.ubuntu.com)

You should be able to find all of php and its deps in there. 

To make a repo CD.[/QUOTE]
Thanks for the excellent lead sir! :) 

I found [http://packages.ubuntu.com/hoary/web/php4](http://packages.ubuntu.com/hoary/web/php4) and it lists libapache2-mod-php4 and php4-common as the things which it is dependent on... however, it doesn't list Flex or Bison which it is asking for when I am trying to compile it. It this thing which I'd download different from compiling? Also, can you suggest which all other packages I may need for it (or a hint how I can find what all other packages I may need along with it).

Thanks a lot again.

---

### Post by KingBahamut on 2005-10-06
Im assuming your trying to compile php4 or 5? 

That link will only give you what runs on the repos, not against what you might be trying to compile.

---

### Post by Lord Brar on 2005-10-06
Bill, I was trying to compile php4. :)

---

### Post by Lord Brar on 2005-10-11
Thanks guys. Downloading packages and creating a local repo worked wonders. :)

---

