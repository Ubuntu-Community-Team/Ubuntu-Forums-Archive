---
title: "Virtual hosts problem.."
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by Hawkowl on 2006-08-07
I have spent the last couple of days installing ubuntu for the first time ever.
I need it to be a webserver and to host many virtual hosts.
 I have tried everything, read as many posts as I could, and just when I think it's all bound to work....nothing.

I have all my sites in the /var/www folder.
My index.html for my main site is there.

I have used Webmin to set up apache and it seems to be running oK
I have used Webmin to set up my virtual hosts also, they all went in Ok.
I filled in my hosts file for my router also.
Now on reboot it doesn't find anything!
It can't even find localhost anymore!
all i get is 404 errors...


Boy this this frustrating, but i'm determined to stick with it.
any ideas please anyone..

---

### Post by fourchannel on 2006-08-07
If you think it won't compromise your system's security could you copy and paste the following files.
```
/etc/apache2/apache2.conf
/etc/apache2/sites-avaliable/* #all files listed in there
/etc/apache2/sites-enabled/* #all files listed in there, and make sure the symbloc links are correct too.
/etc/apache2/ports.conf
``` 
and maybe we can figure out what's up.

---

### Post by Hawkowl on 2006-08-07
Ok thanks...

heres apache2.conf..
```

# Based upon the NCSA server configuration files originally by Rob McCool.
# Changed extensively for the Debian package by Daniel Stone <daniel@sfarc.net>
# and also by Thom May <thom@debian.org>.

# ServerRoot: The top of the directory tree under which the server's
# configuration, error, and log files are kept.
#
# NOTE!  If you intend to place this on an NFS (or otherwise network)
# mounted filesystem then please read the LockFile documentation
# (available at <URL:http://www.apache.org/docs/mod/core.html#lockfile>);
# you will save yourself a lot of trouble.

ServerRoot "/etc/apache2"

# The LockFile directive sets the path to the lockfile used when Apache
# is compiled with either USE_FCNTL_SERIALIZED_ACCEPT or
# USE_FLOCK_SERIALIZED_ACCEPT. This directive should normally be left at
# its default value. The main reason for changing it is if the logs
# directory is NFS mounted, since the lockfile MUST BE STORED ON A LOCAL
# DISK. The PID of the main server process is automatically appended to
# the filename. 

LockFile /var/lock/apache2/accept.lock

# PidFile: The file in which the server should record its process
# identification number when it starts.

PidFile /var/run/apache2.pid

# Timeout: The number of seconds before receives and sends time out.

Timeout 300

# KeepAlive: Whether or not to allow persistent connections (more than
# one request per connection). Set to "Off" to deactivate.

KeepAlive On

# MaxKeepAliveRequests: The maximum number of requests to allow
# during a persistent connection. Set to 0 to allow an unlimited amount.
# We recommend you leave this number high, for maximum performance.

MaxKeepAliveRequests 100

# KeepAliveTimeout: Number of seconds to wait for the next request from the
# same client on the same connection.

KeepAliveTimeout 15

##
## Server-Pool Size Regulation (MPM specific)
## 

# prefork MPM
# StartServers ......... number of server processes to start
# MinSpareServers ...... minimum number of server processes which are kept spare
# MaxSpareServers ...... maximum number of server processes which are kept spare
# MaxClients ........... maximum number of server processes allowed to start
# MaxRequestsPerChild .. maximum number of requests a server process serves
<IfModule prefork.c>
StartServers         5
MinSpareServers      5
MaxSpareServers     10
MaxClients          20
MaxRequestsPerChild  0
</IfModule>

# pthread MPM
# StartServers ......... initial  number of server processes to start
# MaxClients ........... maximum  number of server processes allowed to start
# MinSpareThreads ...... minimum  number of worker threads which are kept spare
# MaxSpareThreads ...... maximum  number of worker threads which are kept spare
# ThreadsPerChild ...... constant number of worker threads in each server process
# MaxRequestsPerChild .. maximum  number of requests a server process serves
<IfModule worker.c>
StartServers         2
MaxClients         150 
MinSpareThreads     25
MaxSpareThreads     75
ThreadsPerChild     25
MaxRequestsPerChild  0
</IfModule>

# perchild MPM
# NumServers ........... constant number of server processes
# StartThreads ......... initial  number of worker threads in each server process
# MinSpareThreads ...... minimum  number of worker threads which are kept spare
# MaxSpareThreads ...... maximum  number of worker threads which are kept spare
# MaxThreadsPerChild ... maximum  number of worker threads in each server process
# MaxRequestsPerChild .. maximum  number of connections per server process (then it dies)
<IfModule perchild.c>
NumServers           5
StartThreads         5
MinSpareThreads      5
MaxSpareThreads     10
MaxThreadsPerChild  20
MaxRequestsPerChild  0
AcceptMutex fcntl
</IfModule>

User www-data
Group www-data

# The following directives define some format nicknames for use with
# a CustomLog directive (see below).
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent


# Global error log.
ErrorLog /var/log/apache2/error.log

# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

# Include all the user configurations:
Include /etc/apache2/httpd.conf

# Include ports listing
Include /etc/apache2/ports.conf

# Include generic snippets of statements
Include /etc/apache2/conf.d/[^.#]*

#Let's have some Icons, shall we?
Alias /icons/ "/usr/share/apache2/icons/"
<Directory "/usr/share/apache2/icons">
    Options Indexes MultiViews
    AllowOverride None
    Order allow,deny
    Allow from all
</Directory>

# Set up the default error docs.
#
# Customizable error responses come in three flavors:
# 1) plain text 2) local redirects 3) external redirects
#
# Some examples:
#ErrorDocument 500 "The server made a boo boo."
#ErrorDocument 404 /missing.html
#ErrorDocument 404 "/cgi-bin/missing_handler.pl"
#ErrorDocument 402 [http://www.example.com/subscription_info.html](http://www.example.com/subscription_info.html)
#

#
# Putting this all together, we can Internationalize error responses.
#
# We use Alias to redirect any /error/HTTP_<error>.html.var response to
# our collection of by-error message multi-language collections.  We use 
# includes to substitute the appropriate text.
#
# You can modify the messages' appearance without changing any of the
# default HTTP_<error>.html.var files by adding the line;
#
#   Alias /error/include/ "/your/include/path/"
#
# which allows you to create your own set of files by starting with the
# /usr/local/apache2/error/include/ files and
# copying them to /your/include/path/, even on a per-VirtualHost basis.
#

<IfModule mod_negotiation.c>
<IfModule mod_include.c>
    Alias /error/ "/usr/share/apache2/error/"

    <Directory "/usr/share/apache2/error">
        AllowOverride None
        Options IncludesNoExec
        AddOutputFilter Includes html
        AddHandler type-map var
        Order allow,deny
        Allow from all
        LanguagePriority en es de fr
        ForceLanguagePriority Prefer Fallback
    </Directory>

    ErrorDocument 400 /error/HTTP_BAD_REQUEST.html.var
    ErrorDocument 401 /error/HTTP_UNAUTHORIZED.html.var
    ErrorDocument 403 /error/HTTP_FORBIDDEN.html.var
    ErrorDocument 404 /error/HTTP_NOT_FOUND.html.var
    ErrorDocument 405 /error/HTTP_METHOD_NOT_ALLOWED.html.var
    ErrorDocument 408 /error/HTTP_REQUEST_TIME_OUT.html.var
    ErrorDocument 410 /error/HTTP_GONE.html.var
    ErrorDocument 411 /error/HTTP_LENGTH_REQUIRED.html.var
    ErrorDocument 412 /error/HTTP_PRECONDITION_FAILED.html.var
    ErrorDocument 413 /error/HTTP_REQUEST_ENTITY_TOO_LARGE.html.var
    ErrorDocument 414 /error/HTTP_REQUEST_URI_TOO_LARGE.html.var
    ErrorDocument 415 /error/HTTP_SERVICE_UNAVAILABLE.html.var
    ErrorDocument 500 /error/HTTP_INTERNAL_SERVER_ERROR.html.var
    ErrorDocument 501 /error/HTTP_NOT_IMPLEMENTED.html.var
    ErrorDocument 502 /error/HTTP_BAD_GATEWAY.html.var
    ErrorDocument 503 /error/HTTP_SERVICE_UNAVAILABLE.html.var
    ErrorDocument 506 /error/HTTP_VARIANT_ALSO_VARIES.html.var

</IfModule>
</IfModule>

DirectoryIndex index.html index.cgi index.pl index.php index.htm index.shtml index.xhtml

# UserDir is now a module
#UserDir public_html
#UserDir disabled root

#<Directory /home/*/public_html>
#	AllowOverride FileInfo AuthConfig Limit
#	Options Indexes SymLinksIfOwnerMatch IncludesNoExec
#</Directory>

AccessFileName .htaccess

<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>

UseCanonicalName Off

TypesConfig /etc/mime.types
DefaultType text/plain

HostnameLookups Off

IndexOptions FancyIndexing VersionSort

AddIconByEncoding (CMP,/icons/compressed.gif) x-compress x-gzip

AddIconByType (TXT,/icons/text.gif) text/*
AddIconByType (IMG,/icons/image2.gif) image/*
AddIconByType (SND,/icons/sound2.gif) audio/*
AddIconByType (VID,/icons/movie.gif) video/*

# This really should be .jpg.

AddIcon /icons/binary.gif .bin .exe
AddIcon /icons/binhex.gif .hqx
AddIcon /icons/tar.gif .tar
AddIcon /icons/world2.gif .wrl .wrl.gz .vrml .vrm .iv
AddIcon /icons/compressed.gif .Z .z .tgz .gz .zip
AddIcon /icons/a.gif .ps .ai .eps
AddIcon /icons/layout.gif .html .shtml .htm .pdf
AddIcon /icons/text.gif .txt
AddIcon /icons/c.gif .c
AddIcon /icons/p.gif .pl .py
AddIcon /icons/f.gif .for
AddIcon /icons/dvi.gif .dvi
AddIcon /icons/uuencoded.gif .uu
AddIcon /icons/script.gif .conf .sh .shar .csh .ksh .tcl
AddIcon /icons/tex.gif .tex
AddIcon /icons/bomb.gif core

AddIcon /icons/back.gif ..
AddIcon /icons/hand.right.gif README
AddIcon /icons/folder.gif ^^DIRECTORY^^
AddIcon /icons/blank.gif ^^BLANKICON^^


# This is from Matty J's patch. Anyone want to make the icons?
#AddIcon /icons/dirsymlink.jpg ^^SYMDIR^^
#AddIcon /icons/symlink.jpg ^^SYMLINK^^

DefaultIcon /icons/unknown.gif

ReadmeName README.html
HeaderName HEADER.html

IndexIgnore .??* *~ *# HEADER* RCS CVS *,t

AddEncoding x-compress Z
AddEncoding x-gzip gz tgz

AddLanguage da .dk
AddLanguage nl .nl
AddLanguage en .en
AddLanguage et .et
AddLanguage fr .fr
AddLanguage de .de
AddLanguage el .el
AddLanguage it .it
AddLanguage ja .ja
AddLanguage pl .po
AddLanguage ko .ko
AddLanguage pt .pt
AddLanguage no .no
AddLanguage pt-br .pt-br
AddLanguage ltz .ltz
AddLanguage ca .ca
AddLanguage es .es
AddLanguage sv .se
AddLanguage cz .cz
AddLanguage ru .ru
AddLanguage tw .tw
AddLanguage zh-tw .tw

LanguagePriority en da nl et fr de el it ja ko no pl pt pt-br ltz ca es sv tw


#AddDefaultCharset	ISO-8859-1

AddCharset ISO-8859-1  .iso8859-1  .latin1
AddCharset ISO-8859-2  .iso8859-2  .latin2 .cen
AddCharset ISO-8859-3  .iso8859-3  .latin3
AddCharset ISO-8859-4  .iso8859-4  .latin4
AddCharset ISO-8859-5  .iso8859-5  .latin5 .cyr .iso-ru
AddCharset ISO-8859-6  .iso8859-6  .latin6 .arb
AddCharset ISO-8859-7  .iso8859-7  .latin7 .grk
AddCharset ISO-8859-8  .iso8859-8  .latin8 .heb	
AddCharset ISO-8859-9  .iso8859-9  .latin9 .trk
AddCharset ISO-2022-JP .iso2022-jp .jis
AddCharset ISO-2022-KR .iso2022-kr .kis
AddCharset ISO-2022-CN .iso2022-cn .cis
AddCharset Big5        .Big5       .big5
# For russian, more than one charset is used (depends on client, mostly):
AddCharset WINDOWS-1251 .cp-1251   .win-1251
AddCharset CP866       .cp866
AddCharset KOI8-r      .koi8-r .koi8-ru
AddCharset KOI8-ru     .koi8-uk .ua
AddCharset ISO-10646-UCS-2 .ucs2
AddCharset ISO-10646-UCS-4 .ucs4
AddCharset UTF-8       .utf8

AddCharset GB2312      .gb2312 .gb 
AddCharset utf-7       .utf7
AddCharset utf-8       .utf8
AddCharset big5	       .big5 .b5
AddCharset EUC-TW      .euc-tw	
AddCharset EUC-JP      .euc-jp
AddCharset EUC-KR      .euc-kr
AddCharset shift_jis   .sjis

#AddType application/x-httpd-php .php
#AddType application/x-httpd-php-source .phps

AddType application/x-tar .tgz

# To use CGI scripts outside /cgi-bin/:
#
#AddHandler cgi-script .cgi

# To use server-parsed HTML files
#
<FilesMatch "\.shtml(\..+)?$">
    SetOutputFilter INCLUDES
</FilesMatch>

# If you wish to use server-parsed imagemap files, use
#
#AddHandler imap-file map

BrowserMatch "Mozilla/2" nokeepalive
BrowserMatch "MSIE 4\.0b2;" nokeepalive downgrade-1.0 force-response-1.0
BrowserMatch "RealPlayer 4\.0" force-response-1.0
BrowserMatch "Java/1\.0" force-response-1.0
BrowserMatch "JDK/1\.0" force-response-1.0

#
# The following directive disables redirects on non-GET requests for
# a directory that does not include the trailing slash.  This fixes a 
# problem with Microsoft WebFolders which does not appropriately handle 
# redirects for folders with DAV methods.
#

BrowserMatch "Microsoft Data Access Internet Publishing Provider" redirect-carefully
BrowserMatch "^WebDrive" redirect-carefully
BrowserMatch "^gnome-vfs" redirect-carefully 
BrowserMatch "^WebDAVFS/1.[012]" redirect-carefully

# Allow server status reports, with the URL of [http://servername/server-status](http://servername/server-status)
# Change the ".your_domain.com" to match your domain to enable.
#
#<Location /server-status>
#    SetHandler server-status
#    Order deny,allow
#    Deny from all
#    Allow from .your_domain.com
#</Location>

# Allow remote server configuration reports, with the URL of
#  [http://servername/server-info](http://servername/server-info) (requires that mod_info.c be loaded).
# Change the ".your_domain.com" to match your domain to enable.
#
#<Location /server-info>
#    SetHandler server-info
#    Order deny,allow
#    Deny from all
#    Allow from .your_domain.com
#</Location>

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/[^.#]*

```

---

### Post by Hawkowl on 2006-08-07
and heres site available..
```

/etc/apache2/sites-available/36chambers.com.au.conf
/etc/apache2/sites-available/amberwoodworking.com.au.conf
/etc/apache2/sites-available/ballisticdesigns.com.au.conf
/etc/apache2/sites-available/breensfurnitureone.com.conf
/etc/apache2/sites-available/casinoautoelec.com.conf
/etc/apache2/sites-available/casinoflorist.com.au.conf
/etc/apache2/sites-available/casinosmashrepairs.com.conf
/etc/apache2/sites-available/default
/etc/apache2/sites-available/downtowncentral.com.au.conf
/etc/apache2/sites-available/downtowncentral.conf
/etc/apache2/sites-available/eastlandsewingcentre.com.conf
/etc/apache2/sites-available/ianhallidayproshop.com.conf
/etc/apache2/sites-available/lismoremusiccentre.com.conf
/etc/apache2/sites-available/matreshkaswhisperingoaks.com.conf
/etc/apache2/sites-available/mayleyhouse.com.conf
/etc/apache2/sites-available/richmondvalleypetsupplies.com.conf
/etc/apache2/sites-available/www.36chambers.com.au.conf
/etc/apache2/sites-available/www.amberwoodworking.com.au.conf
/etc/apache2/sites-available/www.ballisticdesigns.com.au.conf
/etc/apache2/sites-available/www.breensfurnitureone.com.conf
/etc/apache2/sites-available/www.casinoautoelec.com.conf
/etc/apache2/sites-available/www.casinoflorist.com.au.conf
/etc/apache2/sites-available/www.casinosmashrepairs.com.conf
/etc/apache2/sites-available/www.downtowncentral.com.au.conf
/etc/apache2/sites-available/www.eastlandsewingcentre.com.conf
/etc/apache2/sites-available/www.ianhallidayproshop.com.conf
/etc/apache2/sites-available/www.lismoremusiccentre.com.conf
/etc/apache2/sites-available/www.matreshkaswhisperingoaks.com.conf
/etc/apache2/sites-available/www.mayleyhouse.com.conf
/etc/apache2/sites-available/www.richmondvalleypetsupplies.com.conf

```

---

### Post by Hawkowl on 2006-08-07
sites enabled..
```

/etc/apache2/sites-enabled/000-default

```

---

### Post by Hawkowl on 2006-08-07
and lastly ports.conf..
```

Listen 80

```

---

### Post by fourchannel on 2006-08-07
ok i think I know what the problem is...

Here's the setup normally used by virtual hosting.

you have 2 directories "sites-avaliable" and "sites-enabled"

the "sites-avalibale" is saying *i'm the folder that has the configuration files for **each** separate virtual host*

and the "sites-enabled" folder works like this.

If I want to active my virtual host "astronomy.com" then I have to make something called a symlink that I put in the "sites-enabled" and it links over to the configuration file in the "sites-avaliable" directory.

The first thing you need to do is go to the apache2 directory. ```
sudo su
cd /etc/apache2/sites-enabled
# and here is the command to make the symlink
ln -s /etc/apache2/sites-avaliable/astronomy.com "002-astronomy.com"
``` 
Here is what I have in my "sites-enabled" folder on my webserver. ```
limewire@limewire sites-enabled]$ ls -Flah
total 8.0K
drwxr-xr-x  2 root root 4.0K 2006-04-30 00:12 ./
drwxr-xr-x  8 root root 4.0K 2005-11-17 06:14 ../
lrwxrwxrwx  1 root root   35 2006-04-08 22:17 080-schism -> /etc/apache2/sites-available/schism
lrwxrwxrwx  1 root root   34 2006-04-08 21:58 081-arael -> /etc/apache2/sites-available/arael
lrwxrwxrwx  1 root root   36 2006-04-08 22:16 082-fissure -> /etc/apache2/sites-available/fissure
lrwxrwxrwx  1 root root   35 2006-04-08 22:27 083-leliel -> /etc/apache2/sites-available/leliel
limewire@limewire sites-enabled]$
``` 
basically, when apache starts up, all it sees in your "sites-enabled" folder is "000-default" and it only enables the default server, (the one if you type in the IP address of the server and not its name).

So for each virtual host you want to have, you must have a symlink pointing to it. If you have 500 virtual hosts, then you will need 500 symlinks. I don't know any quick way to type 30 symlinks up, besides doing it by hand.

You can learn up some about how apache2 does virtual hosting [here]("http://httpd.apache.org/docs/2.0/vhosts/").
and a little about symlinks [here]("http://unixhelp.ed.ac.uk/CGI/man-cgi?ln").

I hope this helps, it took me a long time to get my virtual servers working correctly. Post back if you have anymore problems.

---

### Post by Hawkowl on 2006-08-07
much appreciated i'll give it a go :D

---

### Post by Hawkowl on 2006-08-07
Now the server won't start it gives me this ...

* Starting apache 2.0 web server...
apache2: could not open document config file /etc/apache2/sites-enabled/002-www.downtowncentral.com.au
   ...fail!

this is how my sites-enabled folder looks now...
```

/etc/apache2/sites-enabled/000-default
/etc/apache2/sites-enabled/002-www.downtowncentral.com.au
/etc/apache2/sites-enabled/003-downtowncentral.com.au
/etc/apache2/sites-enabled/004-www.36chambers.com.au
/etc/apache2/sites-enabled/005-36chambers.com.au
/etc/apache2/sites-enabled/006-www.ballisticdesigns.com.au
/etc/apache2/sites-enabled/007-ballisticdesigns.com.au
/etc/apache2/sites-enabled/008-www.amberwoodworking.com.au
/etc/apache2/sites-enabled/009-amberwoodworking.com.au
/etc/apache2/sites-enabled/010-www.richmondvalleypetsupplies.com
/etc/apache2/sites-enabled/011-richmondvalleypetsupplies.com
/etc/apache2/sites-enabled/012-www.ianhallidayproshop.com
/etc/apache2/sites-enabled/013-ianhallidayproshop.com
/etc/apache2/sites-enabled/014-www.eastlandsewingcentre.com
/etc/apache2/sites-enabled/015-eastlandsewingcentre.com
/etc/apache2/sites-enabled/016-www.lismoremusiccentre.com
/etc/apache2/sites-enabled/017-lismoremusiccentre.com
/etc/apache2/sites-enabled/018-www.matreshkaswhisperingoaks.com
/etc/apache2/sites-enabled/019-matreshkaswhisperingoaks.com
/etc/apache2/sites-enabled/020-www.casinosmashrepairs.com
/etc/apache2/sites-enabled/021-casinosmashrepairs.com
/etc/apache2/sites-enabled/022-www.breensfurnitureone.com
/etc/apache2/sites-enabled/023-breensfurnitureone.com
/etc/apache2/sites-enabled/024-www.casinoautoelec.com
/etc/apache2/sites-enabled/025-casinoautoelec.com
/etc/apache2/sites-enabled/026-www.casinoflorist.com
/etc/apache2/sites-enabled/027-casinoflorist.com
/etc/apache2/sites-enabled/028-www.mayleyhouse.com
/etc/apache2/sites-enabled/029-mayleyhouse.com

```

any idea what going wrong?

---

### Post by fourchannel on 2006-08-07
not sure but could you run these 2 commands and copy and paste what they output here. Remember you can cram alot of code into a post if you use the ```
 tags.

[code]ls -Flah /etc/apache2/sites-available/
``` and ```
ls -Flah /etc/apache2/sites-enabled/
``` 
I think either the file permissions or the symlinks might not be setup correctly. Those two commands will lets us see if that's the case.

---

### Post by Hawkowl on 2006-08-07
ok:
this is sites available
```

drwxr-xr-x 3 root   root   4.0K 2006-08-08 07:36 ./
drwxr-xr-x 8 root   root   4.0K 2006-08-07 17:01 ../
-rw-r--r-- 1 root   root    175 2006-08-07 15:34 36chambers.com.au.conf
-rw-r--r-- 1 root   root    171 2006-08-07 15:35 amberwoodworking.com.au.conf
-rw-r--r-- 1 root   root    179 2006-08-07 15:36 ballisticdesigns.com.au.conf
-rw-r--r-- 1 root   root    172 2006-08-07 15:36 breensfurnitureone.com.conf
-rw-r--r-- 1 root   root    172 2006-08-07 15:37 casinoautoelec.com.conf
-rw-r--r-- 1 root   root    172 2006-08-07 15:37 casinoflorist.com.au.conf
-rw-r--r-- 1 root   root    170 2006-08-07 15:38 casinosmashrepairs.com.conf
-rw-r--r-- 1 root   root     18 2006-08-07 21:22 default
-rw-r--r-- 1 root   root    158 2006-08-07 15:38 downtowncentral.com.au.conf
-rw-r--r-- 1 root   root    151 2006-08-07 21:56 downtowncentral.conf
-rw-r--r-- 1 root   root    178 2006-08-07 15:38 eastlandsewingcentre.com.conf
-rw-r--r-- 1 root   root    174 2006-08-07 15:39 ianhallidayproshop.com.conf
-rw-r--r-- 1 root   root    184 2006-08-07 15:39 lismoremusiccentre.com.conf
-rw-r--r-- 1 root   root    186 2006-08-07 14:37 matreshkaswhisperingoaks.com.co nf
-rw-r--r-- 1 root   root    165 2006-08-07 15:39 mayleyhouse.com.conf
-rw-r--r-- 1 root   root    189 2006-08-07 15:40 richmondvalleypetsupplies.com.c onf
drwxr-xr-x 2 darren darren 4.0K 2006-08-07 21:08 sites-available/
-rw-r--r-- 1 root   root    179 2006-08-07 15:40 www.36chambers.com.au.conf
-rw-r--r-- 1 root   root    175 2006-08-07 15:41 www.amberwoodworking.com.au.con f
-rw-r--r-- 1 root   root    183 2006-08-07 15:41 www.ballisticdesigns.com.au.con f
-rw-r--r-- 1 root   root    176 2006-08-07 15:41 www.breensfurnitureone.com.conf
-rw-r--r-- 1 root   root    176 2006-08-07 15:42 www.casinoautoelec.com.conf
-rw-r--r-- 1 root   root    176 2006-08-07 15:42 www.casinoflorist.com.au.conf
-rw-r--r-- 1 root   root    174 2006-08-07 15:42 www.casinosmashrepairs.com.conf
-rw-r--r-- 1 root   root    183 2006-08-07 21:55 www.downtowncentral.com.au.conf
-rw-r--r-- 1 root   root    223 2006-08-07 21:08 www.downtowncentral.com.au.conf ~
-rw-r--r-- 1 root   root    180 2006-08-07 21:03 www.downtowncentral.com.au.conf ~~
-rw-r--r-- 1 root   root    182 2006-08-07 15:43 www.eastlandsewingcentre.com.co nf
-rw-r--r-- 1 root   root    178 2006-08-07 15:43 www.ianhallidayproshop.com.conf
-rw-r--r-- 1 root   root    188 2006-08-07 15:44 www.lismoremusiccentre.com.conf
-rw-r--r-- 1 root   root    190 2006-08-07 15:44 www.matreshkaswhisperingoaks.co m.conf
-rw-r--r-- 1 root   root    338 2006-08-07 15:44 www.mayleyhouse.com.conf
-rw-r--r-- 1 root   root    193 2006-08-07 15:45 www.richmondvalleypetsupplies.c om.conf

```

and this is sites enabled:
```

drwxr-xr-x 3 root   root   4.0K 2006-08-08 07:35 ./
drwxr-xr-x 8 root   root   4.0K 2006-08-07 17:01 ../
lrwxrwxrwx 1 root   root     36 2005-01-02 16:18 000-default -> /etc/apache2/sites-available/default
-rw-r--r-- 1 root   root     28 2006-08-07 21:22 000-default~
drwxr-xr-x 2 darren darren 4.0K 2006-08-07 21:22 sites-enabled/

```

hope this helps

---

### Post by fourchannel on 2006-08-07
K hawk I'm pretty sure I see what the problem is. I posted a screenshot below of how I have my setup. I have to run somewhere real quick but I'll come back and walk you through on how to set this up. The problem is, as best as I can tell, is that there are no symlinks in the enabled folder pointing to the virtual hosts.

Symlinks are like shortcuts, they point to other files.

The second thing, the one that is preventing the server from starting, is that there are 2 copies of "000-default" in the enabled folder and that is messing up the server. You need to either move or delete the "000-default~" file, cause the server is trying to load the same "virtual server" twice and it craps out.

Here is a image of how I have my setup. Notice that all the active virtual hosts are listed in the enabled folder. You'll also notice that because they are listed in light blue, they are shortcuts. So every thing i have listed in the enabled folder is really a shortcut to the actual files in the sites-avaliable folder.

I'll come back and help you out in a little bit, I hope this helps in the meantime.

---

### Post by Hawkowl on 2006-08-07
I deleted the old Apache2 and reinstalled it.
I can get Apache to run, but still cannot get it serve a file on the net.
It does open localhost correctly though.
But when I shut down my original server and direct port 80 to this one......nothing.

Here is what the inside of my sites availabe/default file looks like now:
```

NameVirtualHost *
<VirtualHost *>
	ServerAdmin info@downtowncentral.com.au
	
	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# Uncomment this directive is you want to see apache2's
		# default start page (in /apache2-default) when you go to /
		#RedirectMatch ^/$ /apache2-default/
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

<VirtualHost>
DocumentRoot /var/www

```


and this is what the 000.default file looks like in my sites enabled folder ;
```

NameVirtualHost *
<VirtualHost *>
	ServerAdmin info@downtowncentral.com.au
	
	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# Uncomment this directive is you want to see apache2's
		# default start page (in /apache2-default) when you go to /
		#RedirectMatch ^/$ /apache2-default/
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

---

### Post by Hawkowl on 2006-08-07
Here are the results now when i run those 2 command you gave me earlier:

sites available
```

total 16K
drwxr-xr-x 2 root root 4.0K 2006-08-08 11:52 ./
drwxr-xr-x 8 root root 4.0K 2006-08-08 11:11 ../
-rw-r--r-- 1 root root 1.2K 2006-08-08 11:52 default
-rw-r--r-- 1 root root 1.2K 2006-07-27 04:01 default~

```
 sites enabled
```

total 8.0K
drwxr-xr-x 2 root root 4.0K 2006-08-08 11:11 ./
drwxr-xr-x 8 root root 4.0K 2006-08-08 11:11 ../
lrwxrwxrwx 1 root root   36 2006-08-08 11:11 000-default -> /etc/apache2/sites-available/default

```

that last line does have a blue link also

---

### Post by Hawkowl on 2006-08-07
Ok here is apache2.conf
```

# Based upon the NCSA server configuration files originally by Rob McCool.
# Changed extensively for the Debian package by Daniel Stone <daniel@sfarc.net>
# and also by Thom May <thom@debian.org>.

# ServerRoot: The top of the directory tree under which the server's
# configuration, error, and log files are kept.
#
# NOTE!  If you intend to place this on an NFS (or otherwise network)
# mounted filesystem then please read the LockFile documentation
# (available at <URL:http://www.apache.org/docs/mod/core.html#lockfile>);
# you will save yourself a lot of trouble.

ServerRoot "/etc/apache2"

# The LockFile directive sets the path to the lockfile used when Apache
# is compiled with either USE_FCNTL_SERIALIZED_ACCEPT or
# USE_FLOCK_SERIALIZED_ACCEPT. This directive should normally be left at
# its default value. The main reason for changing it is if the logs
# directory is NFS mounted, since the lockfile MUST BE STORED ON A LOCAL
# DISK. The PID of the main server process is automatically appended to
# the filename. 

LockFile /var/lock/apache2/accept.lock

# PidFile: The file in which the server should record its process
# identification number when it starts.

PidFile /var/run/apache2.pid

# Timeout: The number of seconds before receives and sends time out.

Timeout 300

# KeepAlive: Whether or not to allow persistent connections (more than
# one request per connection). Set to "Off" to deactivate.

KeepAlive On

# MaxKeepAliveRequests: The maximum number of requests to allow
# during a persistent connection. Set to 0 to allow an unlimited amount.
# We recommend you leave this number high, for maximum performance.

MaxKeepAliveRequests 100

# KeepAliveTimeout: Number of seconds to wait for the next request from the
# same client on the same connection.

KeepAliveTimeout 15

##
## Server-Pool Size Regulation (MPM specific)
## 

# prefork MPM
# StartServers ......... number of server processes to start
# MinSpareServers ...... minimum number of server processes which are kept spare
# MaxSpareServers ...... maximum number of server processes which are kept spare
# MaxClients ........... maximum number of server processes allowed to start
# MaxRequestsPerChild .. maximum number of requests a server process serves
<IfModule prefork.c>
StartServers         5
MinSpareServers      5
MaxSpareServers     10
MaxClients          20
MaxRequestsPerChild  0
</IfModule>

# pthread MPM
# StartServers ......... initial  number of server processes to start
# MaxClients ........... maximum  number of server processes allowed to start
# MinSpareThreads ...... minimum  number of worker threads which are kept spare
# MaxSpareThreads ...... maximum  number of worker threads which are kept spare
# ThreadsPerChild ...... constant number of worker threads in each server process
# MaxRequestsPerChild .. maximum  number of requests a server process serves
<IfModule worker.c>
StartServers         2
MaxClients         150 
MinSpareThreads     25
MaxSpareThreads     75
ThreadsPerChild     25
MaxRequestsPerChild  0
</IfModule>

# perchild MPM
# NumServers ........... constant number of server processes
# StartThreads ......... initial  number of worker threads in each server process
# MinSpareThreads ...... minimum  number of worker threads which are kept spare
# MaxSpareThreads ...... maximum  number of worker threads which are kept spare
# MaxThreadsPerChild ... maximum  number of worker threads in each server process
# MaxRequestsPerChild .. maximum  number of connections per server process (then it dies)
<IfModule perchild.c>
NumServers           5
StartThreads         5
MinSpareThreads      5
MaxSpareThreads     10
MaxThreadsPerChild  20
MaxRequestsPerChild  0
AcceptMutex fcntl
</IfModule>

User www-data
Group www-data

# The following directives define some format nicknames for use with
# a CustomLog directive (see below).
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent


# Global error log.
ErrorLog /var/log/apache2/error.log

# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

# Include all the user configurations:
Include /etc/apache2/httpd.conf

# Include ports listing
Include /etc/apache2/ports.conf

# Include generic snippets of statements
Include /etc/apache2/conf.d/[^.#]*

#Let's have some Icons, shall we?
Alias /icons/ "/usr/share/apache2/icons/"
<Directory "/usr/share/apache2/icons">
    Options Indexes MultiViews
    AllowOverride None
    Order allow,deny
    Allow from all
</Directory>

# Set up the default error docs.
#
# Customizable error responses come in three flavors:
# 1) plain text 2) local redirects 3) external redirects
#
# Some examples:
#ErrorDocument 500 "The server made a boo boo."
#ErrorDocument 404 /missing.html
#ErrorDocument 404 "/cgi-bin/missing_handler.pl"
#ErrorDocument 402 http://www.example.com/subscription_info.html
#

#
# Putting this all together, we can Internationalize error responses.
#
# We use Alias to redirect any /error/HTTP_<error>.html.var response to
# our collection of by-error message multi-language collections.  We use 
# includes to substitute the appropriate text.
#
# You can modify the messages' appearance without changing any of the
# default HTTP_<error>.html.var files by adding the line;
#
#   Alias /error/include/ "/your/include/path/"
#
# which allows you to create your own set of files by starting with the
# /usr/local/apache2/error/include/ files and
# copying them to /your/include/path/, even on a per-VirtualHost basis.
#

<IfModule mod_negotiation.c>
<IfModule mod_include.c>
    Alias /error/ "/usr/share/apache2/error/"

    <Directory "/usr/share/apache2/error">
        AllowOverride None
        Options IncludesNoExec
        AddOutputFilter Includes html
        AddHandler type-map var
        Order allow,deny
        Allow from all
        LanguagePriority en es de fr
        ForceLanguagePriority Prefer Fallback
    </Directory>

    ErrorDocument 400 /error/HTTP_BAD_REQUEST.html.var
    ErrorDocument 401 /error/HTTP_UNAUTHORIZED.html.var
    ErrorDocument 403 /error/HTTP_FORBIDDEN.html.var
    ErrorDocument 404 /error/HTTP_NOT_FOUND.html.var
    ErrorDocument 405 /error/HTTP_METHOD_NOT_ALLOWED.html.var
    ErrorDocument 408 /error/HTTP_REQUEST_TIME_OUT.html.var
    ErrorDocument 410 /error/HTTP_GONE.html.var
    ErrorDocument 411 /error/HTTP_LENGTH_REQUIRED.html.var
    ErrorDocument 412 /error/HTTP_PRECONDITION_FAILED.html.var
    ErrorDocument 413 /error/HTTP_REQUEST_ENTITY_TOO_LARGE.html.var
    ErrorDocument 414 /error/HTTP_REQUEST_URI_TOO_LARGE.html.var
    ErrorDocument 415 /error/HTTP_SERVICE_UNAVAILABLE.html.var
    ErrorDocument 500 /error/HTTP_INTERNAL_SERVER_ERROR.html.var
    ErrorDocument 501 /error/HTTP_NOT_IMPLEMENTED.html.var
    ErrorDocument 502 /error/HTTP_BAD_GATEWAY.html.var
    ErrorDocument 503 /error/HTTP_SERVICE_UNAVAILABLE.html.var
    ErrorDocument 506 /error/HTTP_VARIANT_ALSO_VARIES.html.var

</IfModule>
</IfModule>

DirectoryIndex index.html index.cgi index.pl index.php index.xhtml

# UserDir is now a module
#UserDir public_html
#UserDir disabled root

#<Directory /home/*/public_html>
#	AllowOverride FileInfo AuthConfig Limit
#	Options Indexes SymLinksIfOwnerMatch IncludesNoExec
#</Directory>

AccessFileName .htaccess

<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>

UseCanonicalName Off

TypesConfig /etc/mime.types
DefaultType text/plain

HostnameLookups Off

IndexOptions FancyIndexing VersionSort

AddIconByEncoding (CMP,/icons/compressed.gif) x-compress x-gzip

AddIconByType (TXT,/icons/text.gif) text/*
AddIconByType (IMG,/icons/image2.gif) image/*
AddIconByType (SND,/icons/sound2.gif) audio/*
AddIconByType (VID,/icons/movie.gif) video/*

# This really should be .jpg.

AddIcon /icons/binary.gif .bin .exe
AddIcon /icons/binhex.gif .hqx
AddIcon /icons/tar.gif .tar
AddIcon /icons/world2.gif .wrl .wrl.gz .vrml .vrm .iv
AddIcon /icons/compressed.gif .Z .z .tgz .gz .zip
AddIcon /icons/a.gif .ps .ai .eps
AddIcon /icons/layout.gif .html .shtml .htm .pdf
AddIcon /icons/text.gif .txt
AddIcon /icons/c.gif .c
AddIcon /icons/p.gif .pl .py
AddIcon /icons/f.gif .for
AddIcon /icons/dvi.gif .dvi
AddIcon /icons/uuencoded.gif .uu
AddIcon /icons/script.gif .conf .sh .shar .csh .ksh .tcl
AddIcon /icons/tex.gif .tex
AddIcon /icons/bomb.gif core

AddIcon /icons/back.gif ..
AddIcon /icons/hand.right.gif README
AddIcon /icons/folder.gif ^^DIRECTORY^^
AddIcon /icons/blank.gif ^^BLANKICON^^


# This is from Matty J's patch. Anyone want to make the icons?
#AddIcon /icons/dirsymlink.jpg ^^SYMDIR^^
#AddIcon /icons/symlink.jpg ^^SYMLINK^^

DefaultIcon /icons/unknown.gif

ReadmeName README.html
HeaderName HEADER.html

IndexIgnore .??* *~ *# HEADER* RCS CVS *,t

AddEncoding x-compress Z
AddEncoding x-gzip gz tgz

AddLanguage da .dk
AddLanguage nl .nl
AddLanguage en .en
AddLanguage et .et
AddLanguage fr .fr
AddLanguage de .de
AddLanguage el .el
AddLanguage it .it
AddLanguage ja .ja
AddLanguage pl .po
AddLanguage ko .ko
AddLanguage pt .pt
AddLanguage no .no
AddLanguage pt-br .pt-br
AddLanguage ltz .ltz
AddLanguage ca .ca
AddLanguage es .es
AddLanguage sv .se
AddLanguage cz .cz
AddLanguage ru .ru
AddLanguage tw .tw
AddLanguage zh-tw .tw

LanguagePriority en da nl et fr de el it ja ko no pl pt pt-br ltz ca es sv tw


#AddDefaultCharset	ISO-8859-1

AddCharset ISO-8859-1  .iso8859-1  .latin1
AddCharset ISO-8859-2  .iso8859-2  .latin2 .cen
AddCharset ISO-8859-3  .iso8859-3  .latin3
AddCharset ISO-8859-4  .iso8859-4  .latin4
AddCharset ISO-8859-5  .iso8859-5  .latin5 .cyr .iso-ru
AddCharset ISO-8859-6  .iso8859-6  .latin6 .arb
AddCharset ISO-8859-7  .iso8859-7  .latin7 .grk
AddCharset ISO-8859-8  .iso8859-8  .latin8 .heb	
AddCharset ISO-8859-9  .iso8859-9  .latin9 .trk
AddCharset ISO-2022-JP .iso2022-jp .jis
AddCharset ISO-2022-KR .iso2022-kr .kis
AddCharset ISO-2022-CN .iso2022-cn .cis
AddCharset Big5        .Big5       .big5
# For russian, more than one charset is used (depends on client, mostly):
AddCharset WINDOWS-1251 .cp-1251   .win-1251
AddCharset CP866       .cp866
AddCharset KOI8-r      .koi8-r .koi8-ru
AddCharset KOI8-ru     .koi8-uk .ua
AddCharset ISO-10646-UCS-2 .ucs2
AddCharset ISO-10646-UCS-4 .ucs4
AddCharset UTF-8       .utf8

AddCharset GB2312      .gb2312 .gb 
AddCharset utf-7       .utf7
AddCharset utf-8       .utf8
AddCharset big5	       .big5 .b5
AddCharset EUC-TW      .euc-tw	
AddCharset EUC-JP      .euc-jp
AddCharset EUC-KR      .euc-kr
AddCharset shift_jis   .sjis

#AddType application/x-httpd-php .php
#AddType application/x-httpd-php-source .phps

AddType application/x-tar .tgz

# To use CGI scripts outside /cgi-bin/:
#
#AddHandler cgi-script .cgi

# To use server-parsed HTML files
#
<FilesMatch "\.shtml(\..+)?$">
    SetOutputFilter INCLUDES
</FilesMatch>

# If you wish to use server-parsed imagemap files, use
#
#AddHandler imap-file map

BrowserMatch "Mozilla/2" nokeepalive
BrowserMatch "MSIE 4\.0b2;" nokeepalive downgrade-1.0 force-response-1.0
BrowserMatch "RealPlayer 4\.0" force-response-1.0
BrowserMatch "Java/1\.0" force-response-1.0
BrowserMatch "JDK/1\.0" force-response-1.0

#
# The following directive disables redirects on non-GET requests for
# a directory that does not include the trailing slash.  This fixes a 
# problem with Microsoft WebFolders which does not appropriately handle 
# redirects for folders with DAV methods.
#

BrowserMatch "Microsoft Data Access Internet Publishing Provider" redirect-carefully
BrowserMatch "^WebDrive" redirect-carefully
BrowserMatch "^gnome-vfs" redirect-carefully 
BrowserMatch "^WebDAVFS/1.[012]" redirect-carefully

# Allow server status reports, with the URL of http://servername/server-status
# Change the ".your_domain.com" to match your domain to enable.
#
#<Location /server-status>
#    SetHandler server-status
#    Order deny,allow
#    Deny from all
#    Allow from .your_domain.com
#</Location>

# Allow remote server configuration reports, with the URL of
#  http://servername/server-info (requires that mod_info.c be loaded).
# Change the ".your_domain.com" to match your domain to enable.
#
#<Location /server-info>
#    SetHandler server-info
#    Order deny,allow
#    Deny from all
#    Allow from .your_domain.com
#</Location>

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/[^.#]*

```

---

