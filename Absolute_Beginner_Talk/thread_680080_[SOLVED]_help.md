---
title: "[SOLVED] help"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2008-01-27
ok, so i'm having the hardest time ever freaking creating a server on my computer that i can run phpbb on. like i'm doing everything right but nothing is working. so someone told me earlier that i could run LAMP or something throught VMWare. please tell me how. like step by step please...i just really NEED to get this up and running with phpbb

---

### Post by emarkd on 2008-01-27
LAMP is not an operating system, like Ubuntu.  LAMP stands for

Linux
Apache
Mysql
Php

which is the backbone collection of software for most linux-based web servers in use today.  You can install the LAMP stack on your Ubuntu box by going to Synaptic and clicking Edit > Mark Packages by Task... and checking LAMP.

After your LAMP stack is installed,  you can check it by going to your web browser and typing in [http://localhost](http://localhost).

---

### Post by KingWilliam on 2008-01-27
Hey, 

What you friend told is probably that you should set up an entire web sever. There is a very easy way to do that. Ubuntu comes in two editions, the server and the desktop edition. With the desktop edition you have gnome and the entire User Interface. The server edition doesn't come with all the graphical stuff but gives you the ability to install an entire LAMP during the Ubuntu installation.

LAMP is the abbreviation for "Linux Apache ... PHP" (forgot where the M stands for :p) These are all the parts you need to run a good web server. 

So if you don't need the user interface, download the server edition of Ubuntu 7.10 and choose LAMP during the installation. If you do want t keep the interface, just install the regular Ubuntu and install the different parts (Apache and PHP). You can find these in the repository.

Once you have your server I think installing phpBB is just copying files into the WWW folder.

About VMware. Why do you want to use VMware? Do you just want to give it a try or do you really want to set up a server? If you are just doing some tests, VMware is a nice idea. But if you want to really use the server, make it a native installation.

If you need any more info, let me know ;)

---

### Post by RadiationHazard on 2008-01-27
well i want the graphical interface. this is my only computer and i need to be able to use it. haha. but i just looked in synaptic and lamp is installed i installed it in parts from [here]("http://www.howtoforge.com/ubuntu_lamp_for_newbies"). and as you can see from the screen shot that the LAMP server is checked. so i guess i did it right. but when i go to install and setup phpBB it doesn't pick up the mysql? :confused: also a screen shot of that below.

---

### Post by emarkd on 2008-01-27
So you seem to have MySQL installed.  You can check to see if it's running by doing:

```
sudo /etc/init.d/mysql status
```

and if it's not, you can start it by running

```
sudo /etc/init.d/mysql start
```

---

### Post by RadiationHazard on 2008-01-27
i think it's running?


```
jordan@jordan-laptop:~$ sudo /etc/init.d/mysql status
[sudo] password for jordan:
 * /usr/bin/mysqladmin  Ver 8.41 Distrib 5.0.45, for pc-linux-gnu on i486
Copyright (C) 2000-2006 MySQL AB
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL license

Server version          5.0.45-Debian_1ubuntu3.1-log
Protocol version        10
Connection              Localhost via UNIX socket
UNIX socket             /var/run/mysqld/mysqld.sock
Uptime:                 1 hour 31 min 8 sec

Threads: 1  Questions: 5  Slow queries: 0  Opens: 12  Flush tables: 1  Open tables: 6  Queries per second avg: 0.001
jordan@jordan-laptop:~$ 


```

??

---

### Post by emarkd on 2008-01-27
Yep, mysql is running.  Now lets see if PHP sees MySQL.

Make a new file called test.php under /var/www and put this text in it:

<?php
phpinfo();
?>

Now go to your web browser and type [http://localhost/test.php](http://localhost/test.php).  Scroll down and see if PHP is set up properly for MySQL.

---

### Post by RadiationHazard on 2008-01-27
this is what happened.

```
PHP Version 5.2.3-1ubuntu6.3

System 	Linux jordan-laptop 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686
Build Date 	Jan 10 2008 09:24:13
Server API 	Apache 2.0 Handler
Virtual Directory Support 	disabled
Configuration File (php.ini) Path 	/etc/php5/apache2
Loaded Configuration File 	/etc/php5/apache2/php.ini
Scan this dir for additional .ini files 	/etc/php5/apache2/conf.d
additional .ini files parsed 	/etc/php5/apache2/conf.d/pdo.ini
PHP API 	20041225
PHP Extension 	20060613
Zend Extension 	220060519
Debug Build 	no
Thread Safety 	disabled
Zend Memory Manager 	enabled
IPv6 Support 	enabled
Registered PHP Streams 	zip, php, file, data, http, ftp, compress.bzip2, compress.zlib, https, ftps
Registered Stream Socket Transports 	tcp, udp, unix, udg, ssl, sslv3, sslv2, tls
Registered Stream Filters 	string.rot13, string.toupper, string.tolower, string.strip_tags, convert.*, consumed, convert.iconv.*, bzip2.*, zlib.*

Zend logo This program makes use of the Zend Scripting Language Engine:
Zend Engine v2.2.0, Copyright (c) 1998-2007 Zend Technologies

PHP Credits
Configuration
PHP Core
Directive	Local Value	Master Value
allow_call_time_pass_reference	On	On
allow_url_fopen	On	On
allow_url_include	Off	Off
always_populate_raw_post_data	Off	Off
arg_separator.input	&	&
arg_separator.output	&	&
asp_tags	Off	Off
auto_append_file	no value	no value
auto_globals_jit	On	On
auto_prepend_file	no value	no value
browscap	no value	no value
default_charset	no value	no value
default_mimetype	text/html	text/html
define_syslog_variables	Off	Off
disable_classes	no value	no value
disable_functions	no value	no value
display_errors	On	On
display_startup_errors	Off	Off
doc_root	no value	no value
docref_ext	no value	no value
docref_root	no value	no value
enable_dl	On	On
error_append_string	no value	no value
error_log	no value	no value
error_prepend_string	no value	no value
error_reporting	6135	6135
expose_php	On	On
extension_dir	/usr/lib/php5/20060613+lfs	/usr/lib/php5/20060613+lfs
file_uploads	On	On
highlight.bg	#FFFFFF	#FFFFFF
highlight.comment	#FF8000	#FF8000
highlight.default	#0000BB	#0000BB
highlight.html	#000000	#000000
highlight.keyword	#007700	#007700
highlight.string	#DD0000	#DD0000
html_errors	On	On
ignore_repeated_errors	Off	Off
ignore_repeated_source	Off	Off
ignore_user_abort	Off	Off
implicit_flush	Off	Off
include_path	.:/usr/share/php:/usr/share/pear	.:/usr/share/php:/usr/share/pear
log_errors	Off	Off
log_errors_max_len	1024	1024
magic_quotes_gpc	On	On
magic_quotes_runtime	Off	Off
magic_quotes_sybase	Off	Off
mail.force_extra_parameters	no value	no value
max_execution_time	30	30
max_input_nesting_level	64	64
max_input_time	60	60
memory_limit	128M	128M
open_basedir	no value	no value
output_buffering	no value	no value
output_handler	no value	no value
post_max_size	8M	8M
precision	12	12
realpath_cache_size	16K	16K
realpath_cache_ttl	120	120
register_argc_argv	On	On
register_globals	Off	Off
register_long_arrays	On	On
report_memleaks	On	On
report_zend_debug	On	On
safe_mode	Off	Off
safe_mode_exec_dir	no value	no value
safe_mode_gid	Off	Off
safe_mode_include_dir	no value	no value
sendmail_from	no value	no value
sendmail_path	/usr/sbin/sendmail -t -i 	/usr/sbin/sendmail -t -i 
serialize_precision	100	100
short_open_tag	On	On
SMTP	localhost	localhost
smtp_port	25	25
sql.safe_mode	Off	Off
track_errors	Off	Off
unserialize_callback_func	no value	no value
upload_max_filesize	2M	2M
upload_tmp_dir	no value	no value
user_dir	no value	no value
variables_order	EGPCS	EGPCS
xmlrpc_error_number	0	0
xmlrpc_errors	Off	Off
y2k_compliance	On	On
zend.ze1_compatibility_mode	Off	Off

apache2handler
Apache Version 	Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3
Apache API Version 	20051115
Server Administrator 	webmaster@localhost
Hostname:Port 	127.0.1.1:0
User/Group 	www-data(33)/33
Max Requests 	Per Child: 0 - Keep Alive: on - Max Per Connection: 100
Timeouts 	Connection: 300 - Keep-Alive: 15
Virtual Server 	Yes
Server Root 	/etc/apache2
Loaded Modules 	core mod_log_config mod_logio prefork http_core mod_so mod_alias mod_auth_basic mod_authn_file mod_authz_default mod_authz_groupfile mod_authz_host mod_authz_user mod_autoindex mod_cgi mod_dir mod_env mod_mime mod_negotiation mod_php5 mod_setenvif mod_status

Directive	Local Value	Master Value
engine	1	1
last_modified	0	0
xbithack	0	0

Apache Environment
Variable	Value
HTTP_HOST 	localhost
HTTP_USER_AGENT 	Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.11) Gecko/20071204 Ubuntu/7.10 (gutsy) Firefox/2.0.0.11
HTTP_ACCEPT 	text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5
HTTP_ACCEPT_LANGUAGE 	en-us,en;q=0.5
HTTP_ACCEPT_ENCODING 	gzip,deflate
HTTP_ACCEPT_CHARSET 	ISO-8859-1,utf-8;q=0.7,*;q=0.7
HTTP_KEEP_ALIVE 	300
HTTP_CONNECTION 	keep-alive
HTTP_REFERER 	http://ubuntuforums.org/showthread.php?t=680080
PATH 	/usr/local/bin:/usr/bin:/bin
SERVER_SIGNATURE 	<address>Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3 Server at localhost Port 80</address>
SERVER_SOFTWARE 	Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3
SERVER_NAME 	localhost
SERVER_ADDR 	127.0.0.1
SERVER_PORT 	80
REMOTE_ADDR 	127.0.0.1
DOCUMENT_ROOT 	/var/www/
SERVER_ADMIN 	webmaster@localhost
SCRIPT_FILENAME 	/var/www/test.php
REMOTE_PORT 	57989
GATEWAY_INTERFACE 	CGI/1.1
SERVER_PROTOCOL 	HTTP/1.1
REQUEST_METHOD 	GET
QUERY_STRING 	no value
REQUEST_URI 	/test.php
SCRIPT_NAME 	/test.php

HTTP Headers Information
HTTP Request Headers
HTTP Request 	GET /test.php HTTP/1.1
Host 	localhost
User-Agent 	Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.11) Gecko/20071204 Ubuntu/7.10 (gutsy) Firefox/2.0.0.11
Accept 	text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5
Accept-Language 	en-us,en;q=0.5
Accept-Encoding 	gzip,deflate
Accept-Charset 	ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive 	300
Connection 	keep-alive
Referer 	http://ubuntuforums.org/showthread.php?t=680080
HTTP Response Headers
X-Powered-By 	PHP/5.2.3-1ubuntu6.3
Keep-Alive 	timeout=15, max=100
Connection 	Keep-Alive
Transfer-Encoding 	chunked
Content-Type 	text/html

bcmath
BCMath support 	enabled

bz2
BZip2 Support 	Enabled
Stream Wrapper support 	compress.bz2://
Stream Filter support 	bzip2.decompress, bzip2.compress
BZip2 Version 	1.0.4, 20-Dec-2006

calendar
Calendar support 	enabled

ctype
ctype functions 	enabled

date
date/time support 	enabled
"Olson" Timezone Database Version 	2007.5
Timezone Database 	internal
Default timezone 	America/Chicago

Directive	Local Value	Master Value
date.default_latitude	31.7667	31.7667
date.default_longitude	35.2333	35.2333
date.sunrise_zenith	90.583333	90.583333
date.sunset_zenith	90.583333	90.583333
date.timezone	no value	no value

dba
DBA support 	enabled
Supported handlers 	db4

dom
DOM/XML 	enabled
DOM/XML API Version 	20031129
libxml Version 	2.6.30
HTML Support 	enabled
XPath Support 	enabled
XPointer Support 	enabled
Schema Support 	enabled
RelaxNG Support 	enabled

exif
EXIF Support 	enabled
EXIF Version 	1.4 $Id: exif.c,v 1.173.2.5.2.19 2007/02/27 03:04:40 iliaa Exp $
Supported EXIF Version 	0220
Supported filetypes 	JPEG,TIFF

filter
Input Validation and Filtering 	enabled
Revision 	$Revision: 1.52.2.39 $

Directive	Local Value	Master Value
filter.default	unsafe_raw	unsafe_raw
filter.default_flags	no value	no value

ftp
FTP support 	enabled

gettext
GetText Support 	enabled

hash
hash support 	enabled
Hashing Engines 	md2 md4 md5 sha1 sha256 sha384 sha512 ripemd128 ripemd160 ripemd256 ripemd320 whirlpool tiger128,3 tiger160,3 tiger192,3 tiger128,4 tiger160,4 tiger192,4 snefru gost adler32 crc32 crc32b haval128,3 haval160,3 haval192,3 haval224,3 haval256,3 haval128,4 haval160,4 haval192,4 haval224,4 haval256,4 haval128,5 haval160,5 haval192,5 haval224,5 haval256,5

iconv
iconv support 	enabled
iconv implementation 	glibc
iconv library version 	2.6.1

Directive	Local Value	Master Value
iconv.input_encoding	ISO-8859-1	ISO-8859-1
iconv.internal_encoding	ISO-8859-1	ISO-8859-1
iconv.output_encoding	ISO-8859-1	ISO-8859-1

json
json support 	enabled
json version 	1.2.1

libxml
libXML support 	active
libXML Version 	2.6.30
libXML streams 	enabled

mbstring
Multibyte Support 	enabled
Multibyte string engine 	libmbfl
Multibyte (japanese) regex support 	enabled
Multibyte regex (oniguruma) version 	4.4.4
Multibyte regex (oniguruma) backtrack check 	On

mbstring extension makes use of "streamable kanji code filter and converter", which is distributed under the GNU Lesser General Public License version 2.1.

Directive	Local Value	Master Value
mbstring.detect_order	no value	no value
mbstring.encoding_translation	Off	Off
mbstring.func_overload	0	0
mbstring.http_input	pass	pass
mbstring.http_output	pass	pass
mbstring.internal_encoding	no value	no value
mbstring.language	neutral	neutral
mbstring.strict_detection	Off	Off
mbstring.substitute_character	no value	no value

mime_magic
mime_magic support	invalid magic file, disabled

Directive	Local Value	Master Value
mime_magic.debug	Off	Off
mime_magic.magicfile	/usr/share/file/magic.mime	/usr/share/file/magic.mime

openssl
OpenSSL support 	enabled
OpenSSL Version 	OpenSSL 0.9.8e 23 Feb 2007

pcre
PCRE (Perl Compatible Regular Expressions) Support 	enabled
PCRE Library Version 	7.4 2007-09-21

PDO
PDO support	enabled
PDO drivers 	no value

posix
Revision 	$Revision: 1.70.2.3.2.15 $

Reflection
Reflection	enabled
Version 	$Id: php_reflection.c,v 1.164.2.33.2.39 2007/05/29 08:44:05 helly Exp $

session
Session Support 	enabled
Registered save handlers 	files user
Registered serializer handlers 	php php_binary wddx

Directive	Local Value	Master Value
session.auto_start	Off	Off
session.bug_compat_42	On	On
session.bug_compat_warn	On	On
session.cache_expire	180	180
session.cache_limiter	nocache	nocache
session.cookie_domain	no value	no value
session.cookie_httponly	Off	Off
session.cookie_lifetime	0	0
session.cookie_path	/	/
session.cookie_secure	Off	Off
session.entropy_file	no value	no value
session.entropy_length	0	0
session.gc_divisor	100	100
session.gc_maxlifetime	1440	1440
session.gc_probability	0	0
session.hash_bits_per_character	4	4
session.hash_function	0	0
session.name	PHPSESSID	PHPSESSID
session.referer_check	no value	no value
session.save_handler	files	files
session.save_path	/var/lib/php5	/var/lib/php5
session.serialize_handler	php	php
session.use_cookies	On	On
session.use_only_cookies	Off	Off
session.use_trans_sid	0	0

shmop
shmop support 	enabled

SimpleXML
Simplexml support	enabled
Revision 	$Revision: 1.151.2.22.2.26 $
Schema support 	enabled

soap
Soap Client 	enabled
Soap Server 	enabled

Directive	Local Value	Master Value
soap.wsdl_cache	1	1
soap.wsdl_cache_dir	/tmp	/tmp
soap.wsdl_cache_enabled	1	1
soap.wsdl_cache_limit	5	5
soap.wsdl_cache_ttl	86400	86400

sockets
Sockets Support 	enabled

SPL
SPL support	enabled
Interfaces 	Countable, OuterIterator, RecursiveIterator, SeekableIterator, SplObserver, SplSubject
Classes 	AppendIterator, ArrayIterator, ArrayObject, BadFunctionCallException, BadMethodCallException, CachingIterator, DirectoryIterator, DomainException, EmptyIterator, FilterIterator, InfiniteIterator, InvalidArgumentException, IteratorIterator, LengthException, LimitIterator, LogicException, NoRewindIterator, OutOfBoundsException, OutOfRangeException, OverflowException, ParentIterator, RangeException, RecursiveArrayIterator, RecursiveCachingIterator, RecursiveDirectoryIterator, RecursiveFilterIterator, RecursiveIteratorIterator, RecursiveRegexIterator, RegexIterator, RuntimeException, SimpleXMLIterator, SplFileInfo, SplFileObject, SplObjectStorage, SplTempFileObject, UnderflowException, UnexpectedValueException

standard
Regex Library 	Bundled library enabled
Dynamic Library Support 	enabled
Path to sendmail 	/usr/sbin/sendmail -t -i

Directive	Local Value	Master Value
assert.active	1	1
assert.bail	0	0
assert.callback	no value	no value
assert.quiet_eval	0	0
assert.warning	1	1
auto_detect_line_endings	0	0
default_socket_timeout	60	60
safe_mode_allowed_env_vars	PHP_	PHP_
safe_mode_protected_env_vars	LD_LIBRARY_PATH	LD_LIBRARY_PATH
url_rewriter.tags	a=href,area=href,frame=src,input=src,form=,fieldset=	a=href,area=href,frame=src,input=src,form=,fieldset=
user_agent	no value	no value

sysvmsg
sysvmsg support 	enabled
Revision 	$Revision: 1.20.2.3.2.6 $

tokenizer
Tokenizer Support 	enabled

wddx
WDDX Support	enabled
WDDX Session Serializer 	enabled

xml
XML Support 	active
XML Namespace Support 	active
libxml2 Version 	2.6.30

xmlreader
XMLReader 	enabled

xmlwriter
XMLWriter 	enabled

zip
Zip 	enabled
Extension Version 	$Id: php_zip.c,v 1.1.2.33 2007/05/19 22:25:11 pajoye Exp $
Zip version 	2.0.0
Libzip version 	0.7.1

zlib
ZLib Support 	enabled
Stream Wrapper support 	compress.zlib://
Stream Filter support 	zlib.inflate, zlib.deflate
Compiled Version 	1.2.1.1
Linked Version 	1.2.3.3

Directive	Local Value	Master Value
zlib.output_compression	Off	Off
zlib.output_compression_level	-1	-1
zlib.output_handler	no value	no value

Additional Modules
Module Name
sysvsem
sysvshm

Environment
Variable	Value
PATH 	/usr/local/bin:/usr/bin:/bin
LANG 	C
PWD 	/home/jordan

PHP Variables
Variable	Value
_SERVER["HTTP_HOST"]	localhost
_SERVER["HTTP_USER_AGENT"]	Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.11) Gecko/20071204 Ubuntu/7.10 (gutsy) Firefox/2.0.0.11
_SERVER["HTTP_ACCEPT"]	text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5
_SERVER["HTTP_ACCEPT_LANGUAGE"]	en-us,en;q=0.5
_SERVER["HTTP_ACCEPT_ENCODING"]	gzip,deflate
_SERVER["HTTP_ACCEPT_CHARSET"]	ISO-8859-1,utf-8;q=0.7,*;q=0.7
_SERVER["HTTP_KEEP_ALIVE"]	300
_SERVER["HTTP_CONNECTION"]	keep-alive
_SERVER["HTTP_REFERER"]	http://ubuntuforums.org/showthread.php?t=680080
_SERVER["PATH"]	/usr/local/bin:/usr/bin:/bin
_SERVER["SERVER_SIGNATURE"]	<address>Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3 Server at localhost Port 80</address>
_SERVER["SERVER_SOFTWARE"]	Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3
_SERVER["SERVER_NAME"]	localhost
_SERVER["SERVER_ADDR"]	127.0.0.1
_SERVER["SERVER_PORT"]	80
_SERVER["REMOTE_ADDR"]	127.0.0.1
_SERVER["DOCUMENT_ROOT"]	/var/www/
_SERVER["SERVER_ADMIN"]	webmaster@localhost
_SERVER["SCRIPT_FILENAME"]	/var/www/test.php
_SERVER["REMOTE_PORT"]	57989
_SERVER["GATEWAY_INTERFACE"]	CGI/1.1
_SERVER["SERVER_PROTOCOL"]	HTTP/1.1
_SERVER["REQUEST_METHOD"]	GET
_SERVER["QUERY_STRING"]	no value
_SERVER["REQUEST_URI"]	/test.php
_SERVER["SCRIPT_NAME"]	/test.php
_SERVER["PHP_SELF"]	/test.php
_SERVER["REQUEST_TIME"]	1201476282
_SERVER["argv"]	

Array
(
)

_SERVER["argc"]	0
_ENV["PATH"]	/usr/local/bin:/usr/bin:/bin
_ENV["LANG"]	C
_ENV["PWD"]	/home/jordan

PHP License

This program is free software; you can redistribute it and/or modify it under the terms of the PHP License as published by the PHP Group and included in the distribution in the file: LICENSE

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

If you did not receive a copy of the PHP license, or have any questions about PHP licensing, please contact license@php.net.

```

---

### Post by emarkd on 2008-01-27
Well, there's nothing there about MySQL, so I'd say they're not seeing each other.  I'd say this is your problem and it has nothing to do with PHPBB.

Honestly, I'm not sure how to remedy this.  If you used some convoluted method to install your LAMP stack, I think if I were you I'd uninstall it all and use the Synaptic Task Selection option to reinstall everything at once.  Usually this has very good results.

If you do decide to go this route, make sure you uninstall all of the packages with the --purge option so that the config files all get removed as well.

---

### Post by RadiationHazard on 2008-01-27
well i still don't know how to use the terminal really great. so i used this site
[http://www.howtoforge.com/uu buntu_lamp_for_newbies]("http://www.howtoforge.com/ubuntu_lamp_for_newbies")
could you tell me the codes that i need to put into the terminal to get ride of it and start over please??

Thank you!

---

### Post by RadiationHazard on 2008-01-27
never mind.
i figured it out!!
i just replaced install with remove in the terminal code.
and now i've installed lamp server from the synaptic package mananger and it worked. but now i don't know what to put into the boxes.

---

### Post by emarkd on 2008-01-27
Glad you got it working.

I've never used/installed PHPBB,but it looks like you've got to manually create a user and database in mysql for it to use.  Your best bet is to search google for a tutorial on adding users to mysql as well as creating new databases and setting permissions.

---

