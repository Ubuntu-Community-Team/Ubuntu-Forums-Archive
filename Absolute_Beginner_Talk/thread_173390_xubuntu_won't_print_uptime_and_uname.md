---
title: "xubuntu: won't print uptime and uname"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by henrikfromnorway on 2006-05-10
Hello!

I'm running a webserver, and i tried to print my uptime and uname on the index.php-page.

but, i only get a blank field, insted of my uptime.
can anyone help me?

should i turn on safe_mode? (i'm running a WinXP-server too, so this isn't my primary server)

Any good ideas?

---

### Post by henrikfromnorway on 2006-05-10
please, help me!!

---

### Post by henrikfromnorway on 2006-05-23
Bump!

---

### Post by bicchi on 2006-05-23
I am not sure of the code you are trying to run since you didn't attached anything but here is a method that might work. Make sure that from the console you can type uptime and that something comes up.  

First the HTML code
<html>
Server information: <script src="/cgi-bin/uptime.cgi?js"></script>
</html>

-----------------------------------------------------------------------------------------------------------------------

Second the cgi script that goes inside the cgi-bin directory. It also prints the IP address but this is not necessary and can be modified to print also the "uname" (I have named this script: uptime.cgi): 
```

#!/usr/bin/perl --
print "content-type:text/html\n\n";
 
my $html = `uptime`;
$html =~ s/\n+//g;
if ($ENV{QUERY_STRING} =~ /js/) {
  print qq~uptime=('$html and your IP is: <$ENV{REMOTE_ADDR}>');
  document.write(uptime);~; 
}
else{ 
  print $html; 
}

exit;

```
p.s. There is no uptime command in Win XP.

---

### Post by henrikfromnorway on 2006-05-24
i use phpsysinfo with WinXP Pro, so i can see my uptime :P

i had to turn off safe_mode, and download a new php.ini file. so now it works.

---

