---
title: "Writing to database using Perl in Ubuntu"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by wagnermw on 2007-10-30
I am am attempting to write to a MySQL database table.  I am coding in Perl.  This is what I have so far:

#!/usr/bin/perl -w
use DBI;

$fname=<STDIN>;
chomp $fname;
#$user = "wagnermw";
#$password = "*****"

$dbh = DBI->connect("DBI:MYSQL:dev.mis.uwec.edu;database=wagner", "wagnermw", "*****");
$dbh->do("insert into test(name) values('$fname')");
$dbh->disconnect;
exit (0);

When I try to run this from the command line, I dont get an error, but the debuging does not complete either.  Does anyone have any idea where Im going wrong??  Is this even the right place to ask a question like this?

Thanks,
-Mitch

---

### Post by jfinkels on 2007-10-31
> **wagnermw said:**
>  Is this even the right place to ask a question like this?


Try the programming forum :D [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

