---
title: "can't config apache2 to use mod_perl module"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by itisgood on 2006-09-28
hi everyone.

i have tried to use mod_perl to my apache2 server.

i have got mod_perl installed.

but when i add this to the httpd.conf:

LoadModule perl_module /usr/lib/apache2/modules/mod_perl.so

it will have the error:

jyao@jyao-laptop:/usr/local/apache2/bin$ ./apachectl start
httpd: Syntax error on line 55 of /usr/local/apache2/conf/httpd.conf: API module structure `perl_module' in file **/usr/lib/apache2/modules/mod_perl.so is garbled - perhaps this is not an Apache module DSO?**
jyao@jyao-laptop:/usr/local/apache2/bin$

how can i fix it ? is there anything else i need to install or config??

thx for reading my post.

---

### Post by Average Joe on 2006-09-28
Hmm. I don't think apache2 is configured with the httpd.conf file. This used to be the configuration file for Apache 1. Maybe you have installed both server versions (both apache 1 and apache 2)?

My apache 2 configuration file is located at /etc/apache2/apache2.conf. However, the modules are located in the directories /etc/apache2/mods-available and /etc/apache2/mods-enabled.

Also, I (re)start my apache server with the command apache2ctl, not with apachectl (does not exist). That could be another indication that the server versions are mixed up.

I think you should make sure that you use either apache 1 or apache 2, not both.

Hope this helps.

---

### Post by itisgood on 2006-09-29
hey, you are so right, thx alot
i did find another mod_perl.so and it works when i load that one.
thx a lot

but as i proceed further, another problem comes with the mod_perl

i add this line into the httpd.conf

[COLOR="Blue"]LoadModule perl_module /usr/local/apache2/modules/mod_perl.so[/COLOR]

the server still can be started , working fine.

and then i add this startup.pl into the conf file: apache2/conf/ 

--------------------------------------------------------------------------
[COLOR="blue"]#! /usr/bin/perl

use lib '/usr/local/apache2/mod_perl';

use Apache::Registry();
use Apache::Constants();
use CGI ':standard';
use DBI;

print "running good \n";
1;[/COLOR]------------------------------------------------------------------------

and add one more line into the httpd.conf

[COLOR="Blue"]PerlRequire conf/startup.pl[/COLOR]

then, i wont be able to start the server any more. in the error_log

------------------------------------------------------------------------------------------------------------
[Fri Sep 29 05:59:20 2006] [error] [COLOR="Red"]Can't locate loadable object for
module Apache::Constants in @INC [/COLOR](@INC contains:
/usr/local/apache2/mod_perl /etc/perl /usr/local/lib/perl/5.8.7
/usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5
/usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .
/usr/local/apache2) at /usr/local/lib/perl/5.8.7/mod_perl.pm line
14\nCompilation failed in require at /usr/local/lib/perl/5.8.7/Apache.pm
line 6.\nBEGIN failed--compilation aborted at
/usr/local/lib/perl/5.8.7/Apache.pm line 6.\nCompilation failed in
require at /usr/local/lib/perl/5.8.7/Apache/Registry.pm line 2.\nBEGIN
failed--compilation aborted at
/usr/local/lib/perl/5.8.7/Apache/Registry.pm line 2.\nCompilation failed
in require at /usr/local/apache2/conf/startup.pl line 5.\nBEGIN
failed--compilation aborted at /usr/local/apache2/conf/startup.pl line
5.\nCompilation failed in require at (eval 2) line 1.\n
[Fri Sep 29 05:59:20 2006] [error] Can't load Perl file: conf/startup.pl
for server 192.168.0.6:0, exiting...
-------------------------------------------------------------------------------------------------------------------
but i can directly run the startup.pl
>>perl startup.pl
running good
>>
so i think the modules have been installed.


and after keep trying , i noticed that , unless i comment out 
[COLOR="Blue"]#use Apache::Registry();
#use Apache::Counstants();[/COLOR]
otherwise i wont be able to start the server.

another problem is that, although the server can recognize : [COLOR="blue"]PerlRequire[/COLOR] 
but it cannot recognize : [COLOR="Red"]PerFreshRestart[/COLOR]

can you figure out what probably is wrong with my apache2 ?? 
any ideas could help..
thank you for your time

---

