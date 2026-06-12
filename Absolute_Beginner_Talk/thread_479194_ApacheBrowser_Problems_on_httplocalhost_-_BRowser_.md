---
title: "Apache/Browser Problems on http://localhost - BRowser trying to save .PHP Files"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-06-20
Hi, I have some problems with my Apache setting on my localhost. I'm only running this locally for testing purpose, and I can't figure out what is wrong.

I have followed the instructions [here]("http://www.supriyadisw.net/2006/12/lamp-installation-on-ubuntu") for installing my Apache server, PHP and MySQL databases. I have had it working at one point but had to uninstall and re-install again and now it doesnt work.

The problem:
When I go to [http://localhost](http://localhost) in firefox it lists the directories fine, but if I try an open one of my sites or phpmyadmin firefox asks me where I want to save the file as if I were downloading something. It says you are trying to open a PHTML file what should firefox do with it? It simply wont show the webpage, this is the same if I try and acces the page in IE4Linux, so it's not a firefox thing.

EDIT: HTML files work fine, those just open as they are supposed to!

---

### Post by atria on 2007-06-20
Add this to your httpd.conf:
```

AddType application/x-httpd-php .php
AddType application/x-httpd-php .php3
AddType application/x-httpd-php .phtml

```

---

### Post by kasperbs on 2007-06-20
> AddType application/x-httpd-php .php
AddType application/x-httpd-php .php3
AddType application/x-httpd-php .phtml
To the httpd.conf found in /etc/apache2/httpd.conf? That file was tottally blank, is that normal?
Any way I added that and it didn't change anything. I also tried to restart apache but no change?

EDIT I don't know why it thinks Im opening a PHTML file, because it is an PHP file I'm opening.

---

### Post by straps on 2007-06-20
sudo apt-get install libapache2-mod-php5 && sudo /etc/init.d/apache2 restart

worked for me, bye

---

### Post by kasperbs on 2007-06-20
> **straps said:**
> sudo apt-get install libapache2-mod-php5 && sudo /etc/init.d/apache2 restart
bye bye then ;)
It didn't work for me unfortunately, but thanks for sharing

---

### Post by atria on 2007-06-20
The file is not supposed to be blank.
```
find /etc | grep httpd.conf
```
to look for the location of the file.

---

### Post by kasperbs on 2007-06-20
Yeah the command says that the file is located in /etc/apache2/httpd.conf
And that file is blank?

---

### Post by scxtt on 2007-06-20
you may not need to use httpd.conf ... check for an apache2.conf, i think the install ubuntu does uses that file, but supplies a httpd.conf for legacy-type support/config ...

---

### Post by atria on 2007-06-20
Oops, that might be it. Thanks for the correction scxtt.

---

### Post by kasperbs on 2007-06-20
> **scxtt said:**
> you may not need to use httpd.conf ... check for an apache2.conf, i think the install ubuntu does uses that file, but supplies a httpd.conf for legacy-type support/config ...

Yeah I found a apache2.conf file in that same directory. Here it is:
> #
# Based upon the NCSA server configuration files originally by Rob McCool.
#
# This is the main Apache server configuration file.  It contains the
# configuration directives that give the server its instructions.
# See <URL:http://httpd.apache.org/docs-2.1/> for detailed information about
# the directives.
#
# Do NOT simply read the instructions in here without understanding
# what they do.  They're here only as hints or reminders.  If you are unsure
# consult the online docs. You have been warned.  
#
# The configuration directives are grouped into three basic sections:
#  1. Directives that control the operation of the Apache server process as a
#     whole (the 'global environment').
#  2. Directives that define the parameters of the 'main' or 'default' server,
#     which responds to requests that aren't handled by a virtual host.
#     These directives also provide default values for the settings
#     of all virtual hosts.
#  3. Settings for virtual hosts, which allow Web requests to be sent to
#     different IP addresses or hostnames and have them handled by the
#     same Apache server process.
#
# Configuration and logfile names: If the filenames you specify for many
# of the server's control files begin with "/" (or "drive:/" for Win32), the
# server will use that explicit path.  If the filenames do *not* begin
# with "/", the value of ServerRoot is prepended -- so "/var/log/apache2/foo.log"
# with ServerRoot set to "" will be interpreted by the
# server as "//var/log/apache2/foo.log".
#

### Section 1: Global Environment
#
# The directives in this section affect the overall operation of Apache,
# such as the number of concurrent requests it can handle or where it
# can find its configuration files.
#

#
# ServerRoot: The top of the directory tree under which the server's
# configuration, error, and log files are kept.
#
# NOTE!  If you intend to place this on an NFS (or otherwise network)
# mounted filesystem then please read the LockFile documentation (available
# at <URL:http://httpd.apache.org/docs-2.1/mod/mpm_common.html#lockfile>);
# you will save yourself a lot of trouble.
#
# Do NOT add a slash at the end of the directory path.
#
ServerRoot "/etc/apache2"

#
# The accept serialization lock file MUST BE STORED ON A LOCAL DISK.
#
#<IfModule !mpm_winnt.c>
#<IfModule !mpm_netware.c>
LockFile /var/lock/apache2/accept.lock
#</IfModule>
#</IfModule>

#
# PidFile: The file in which the server should record its process
# identification number when it starts.
#
PidFile /var/run/apache2.pid

#
# Timeout: The number of seconds before receives and sends time out.
#
Timeout 300

#
# KeepAlive: Whether or not to allow persistent connections (more than
# one request per connection). Set to "Off" to deactivate.
#
KeepAlive On

#
# MaxKeepAliveRequests: The maximum number of requests to allow
# during a persistent connection. Set to 0 to allow an unlimited amount.
# We recommend you leave this number high, for maximum performance.
#
MaxKeepAliveRequests 100

#
# KeepAliveTimeout: Number of seconds to wait for the next request from the
# same client on the same connection.
#
KeepAliveTimeout 15

##
## Server-Pool Size Regulation (MPM specific)
## 

# prefork MPM
# StartServers: number of server processes to start
# MinSpareServers: minimum number of server processes which are kept spare
# MaxSpareServers: maximum number of server processes which are kept spare
# MaxClients: maximum number of server processes allowed to start
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

# worker MPM
# StartServers: initial number of server processes to start
# MaxClients: maximum number of simultaneous client connections
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadsPerChild: constant number of worker threads in each server process
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_worker_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>

User www-data
Group www-data

#
# AccessFileName: The name of the file to look for in each directory
# for additional configuration directives.  See also the AllowOverride
# directive.
#

AccessFileName .htaccess

#
# The following lines prevent .htaccess and .htpasswd files from being 
# viewed by Web clients. 
#
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>

TypesConfig /etc/mime.types

#
# DefaultType is the default MIME type the server will use for a document
# if it cannot otherwise determine one, such as from filename extensions.
# If your server contains mostly text or HTML documents, "text/plain" is
# a good value.  If most of your content is binary, such as applications
# or images, you may want to use "application/octet-stream" instead to
# keep browsers from trying to display binary files as though they are
# text.
#
DefaultType text/plain


#
# HostnameLookups: Log the names of clients or just their IP addresses
# e.g., [www.apache.org](www.apache.org) (on) or 204.62.129.132 (off).
# The default is off because it'd be overall better for the net if people
# had to knowingly turn this feature on, since enabling it means that
# each client request will result in AT LEAST one lookup request to the
# nameserver.
#
HostnameLookups Off

# ErrorLog: The location of the error log file.
# If you do not specify an ErrorLog directive within a <VirtualHost>
# container, error messages relating to that virtual host will be
# logged here.  If you *do* define an error logfile for a <VirtualHost>
# container, that host's errors will be logged there and not here.
#
ErrorLog /var/log/apache2/error.log

#
# LogLevel: Control the number of messages logged to the error_log.
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
#
LogLevel warn

# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

# Include all the user configurations:
Include /etc/apache2/httpd.conf

# Include ports listing
Include /etc/apache2/ports.conf

# Include generic snippets of statements
Include /etc/apache2/conf.d/

#
# The following directives define some format nicknames for use with
# a CustomLog directive (see below).
#
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

#
# ServerTokens
# This directive configures what you return as the Server HTTP response
# Header. The default is 'Full' which sends information about the OS-Type
# and compiled in modules.
# Set to one of:  Full | OS | Minor | Minimal | Major | Prod
# where Full conveys the most information, and Prod the least.
#
ServerTokens Full

#
# Optionally add a line containing the server version and virtual host
# name to server-generated pages (internal error documents, FTP directory 
# listings, mod_status and mod_info output etc., but not CGI generated 
# documents or custom error documents).
# Set to "EMail" to also include a mailto: link to the ServerAdmin.
# Set to one of:  On | Off | EMail
#
ServerSignature On

<IfModule alias_module>
    #
    # Aliases: Add here as many aliases as you need (with no limit). The format is 
    # Alias fakename realname
    #
    # Note that if you include a trailing / on fakename then the server will
    # require it to be present in the URL.  So "/icons" isn't aliased in this
    # example, only "/icons/".  If the fakename is slash-terminated, then the 
    # realname must also be slash terminated, and if the fakename omits the 
    # trailing slash, the realname must also omit it.
    #
    # We include the /icons/ alias for FancyIndexed directory listings.  If
    # you do not use FancyIndexing, you may comment this out.
    #
    Alias /icons/ "/usr/share/apache2/icons/"

    <Directory "/usr/share/apache2/icons">
        Options Indexes MultiViews
        AllowOverride None
        Order allow,deny
        Allow from all
    </Directory>

</IfModule>

#
# Directives controlling the display of server-generated directory listings.
#
<IfModule mod_autoindex.c>

    #
    # IndexOptions: Controls the appearance of server-generated directory
    # listings.
    #
    IndexOptions FancyIndexing VersionSort HTMLTable NameWidth=*

    #
    # AddIcon* directives tell the server which icon to show for different
    # files or filename extensions.  These are only displayed for
    # FancyIndexed directories.
    #
    AddIconByEncoding (CMP,/icons/compressed.gif) x-compress x-gzip

    AddIconByType (TXT,/icons/text.gif) text/*
    AddIconByType (IMG,/icons/image2.gif) image/*
    AddIconByType (SND,/icons/sound2.gif) audio/*
    AddIconByType (VID,/icons/movie.gif) video/*

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

    #
    # DefaultIcon is which icon to show for files which do not have an icon
    # explicitly set.
    #
    DefaultIcon /icons/unknown.gif

    #
    # AddDescription allows you to place a short description after a file in
    # server-generated indexes.  These are only displayed for FancyIndexed
    # directories.
    # Format: AddDescription "description" filename
    #
    #AddDescription "GZIP compressed document" .gz
    #AddDescription "tar archive" .tar
    #AddDescription "GZIP compressed tar archive" .tgz

    #
    # ReadmeName is the name of the README file the server will look for by
    # default, and append to directory listings.
    #
    # HeaderName is the name of a file which should be prepended to
    # directory indexes. 
    ReadmeName README.html
    HeaderName HEADER.html

    #
    # IndexIgnore is a set of filenames which directory indexing should ignore
    # and not include in the listing.  Shell-style wildcarding is permitted.
    #
    IndexIgnore .??* *~ *# RCS CVS *,v *,t 
</IfModule>

<IfModule mod_mime.c>

    #
    # AddType allows you to add to or override the MIME configuration
    # file mime.types for specific file types.
    #
    #AddType application/x-gzip .tgz
    #
    # AddEncoding allows you to have certain browsers uncompress
    # information on the fly. Note: Not all browsers support this.
    # Despite the name similarity, the following Add* directives have
    # nothing to do with the FancyIndexing customization directives above.
    #
    #AddEncoding x-compress .Z
    #AddEncoding x-gzip .gz .tgz
    #
    # If the AddEncoding directives above are commented-out, then you
    # probably should define those extensions to indicate media types:
    #
    AddType application/x-compress .Z
    AddType application/x-gzip .gz .tgz

    #
    # DefaultLanguage and AddLanguage allows you to specify the language of 
    # a document. You can then use content negotiation to give a browser a 
    # file in a language the user can understand.
    #
    # Specify a default language. This means that all data
    # going out without a specific language tag (see below) will 
    # be marked with this one. You probably do NOT want to set
    # this unless you are sure it is correct for all cases.
    #
    # * It is generally better to not mark a page as 
    # * being a certain language than marking it with the wrong
    # * language!
    #
    # DefaultLanguage nl
    #
    # Note 1: The suffix does not have to be the same as the language
    # keyword --- those with documents in Polish (whose net-standard
    # language code is pl) may wish to use "AddLanguage pl .po" to
    # avoid the ambiguity with the common suffix for perl scripts.
    #
    # Note 2: The example entries below illustrate that in some cases 
    # the two character 'Language' abbreviation is not identical to 
    # the two character 'Country' code for its country,
    # E.g. 'Danmark/dk' versus 'Danish/da'.
    #
    # Note 3: In the case of 'ltz' we violate the RFC by using a three char
    # specifier. There is 'work in progress' to fix this and get
    # the reference data for rfc1766 cleaned up.
    #
    # Catalan (ca) - Croatian (hr) - Czech (cs) - Danish (da) - Dutch (nl)
    # English (en) - Esperanto (eo) - Estonian (et) - French (fr) - German (de)
    # Greek-Modern (el) - Hebrew (he) - Italian (it) - Japanese (ja)
    # Korean (ko) - Luxembourgeois* (ltz) - Norwegian Nynorsk (nn)
    # Norwegian (no) - Polish (pl) - Portugese (pt)
    # Brazilian Portuguese (pt-BR) - Russian (ru) - Swedish (sv)
    # Simplified Chinese (zh-CN) - Spanish (es) - Traditional Chinese (zh-TW)
    #
    AddLanguage ca .ca
    AddLanguage cs .cz .cs
    AddLanguage da .dk
    AddLanguage de .de
    AddLanguage el .el
    AddLanguage en .en
    AddLanguage eo .eo
    AddLanguage es .es
    AddLanguage et .et
    AddLanguage fr .fr
    AddLanguage he .he
    AddLanguage hr .hr
    AddLanguage it .it
    AddLanguage ja .ja
    AddLanguage ko .ko
    AddLanguage ltz .ltz
    AddLanguage nl .nl
    AddLanguage nn .nn
    AddLanguage no .no
    AddLanguage pl .po
    AddLanguage pt .pt
    AddLanguage pt-BR .pt-br
    AddLanguage ru .ru
    AddLanguage sv .sv
    AddLanguage zh-CN .zh-cn
    AddLanguage zh-TW .zh-tw
</IfModule>

<IfModule mod_negotiation.c>
    #
    # LanguagePriority allows you to give precedence to some languages
    # in case of a tie during content negotiation.
    #
    # Just list the languages in decreasing order of preference. We have
    # more or less alphabetized them here. You probably want to change this.
    #
    LanguagePriority en ca cs da de el eo es et fr he hr it ja ko ltz nl nn no pl pt pt-BR ru sv zh-CN zh-TW

    #
    # ForceLanguagePriority allows you to serve a result page rather than
    # MULTIPLE CHOICES (Prefer) [in case of a tie] or NOT ACCEPTABLE (Fallback)
    # [in case no accepted languages matched the available variants]
    #
    ForceLanguagePriority Prefer Fallback

</IfModule>

<IfModule mod_mime.c>
    #
    # Specify a default charset for all pages sent out. This is
    # always a good idea and opens the door for future internationalisation
    # of your web site, should you ever want it. Specifying it as
    # a default does little harm; as the standard dictates that a page
    # is in iso-8859-1 (latin1) unless specified otherwise i.e. you
    # are merely stating the obvious. There are also some security
    # reasons in browsers, related to javascript and URL parsing
    # which encourage you to always set a default char set.
    #
    #AddDefaultCharset ISO-8859-1

    #
    # Commonly used filename extensions to character sets. You probably
    # want to avoid clashes with the language extensions, unless you
    # are good at carefully testing your setup after each change.
    # See [http://www.iana.org/assignments/character-sets](http://www.iana.org/assignments/character-sets) for the
    # official list of charset names and their respective RFCs.
    #
    AddCharset us-ascii    .ascii .us-ascii
    AddCharset ISO-8859-1  .iso8859-1  .latin1
    AddCharset ISO-8859-2  .iso8859-2  .latin2 .cen
    AddCharset ISO-8859-3  .iso8859-3  .latin3
    AddCharset ISO-8859-4  .iso8859-4  .latin4
    AddCharset ISO-8859-5  .iso8859-5  .cyr .iso-ru
    AddCharset ISO-8859-6  .iso8859-6  .arb .arabic
    AddCharset ISO-8859-7  .iso8859-7  .grk .greek
    AddCharset ISO-8859-8  .iso8859-8  .heb .hebrew
    AddCharset ISO-8859-9  .iso8859-9  .latin5 .trk
    AddCharset ISO-8859-10  .iso8859-10  .latin6
    AddCharset ISO-8859-13  .iso8859-13
    AddCharset ISO-8859-14  .iso8859-14  .latin8
    AddCharset ISO-8859-15  .iso8859-15  .latin9
    AddCharset ISO-8859-16  .iso8859-16  .latin10
    AddCharset ISO-2022-JP .iso2022-jp .jis
    AddCharset ISO-2022-KR .iso2022-kr .kis
    AddCharset ISO-2022-CN .iso2022-cn .cis
    AddCharset Big5        .Big5       .big5 .b5
    AddCharset cn-Big5     .cn-big5
    # For russian, more than one charset is used (depends on client, mostly):
    AddCharset WINDOWS-1251 .cp-1251   .win-1251
    AddCharset CP866       .cp866
    AddCharset KOI8      .koi8
    AddCharset KOI8-E      .koi8-e
    AddCharset KOI8-r      .koi8-r .koi8-ru
    AddCharset KOI8-U      .koi8-u
    AddCharset KOI8-ru     .koi8-uk .ua
    AddCharset ISO-10646-UCS-2 .ucs2
    AddCharset ISO-10646-UCS-4 .ucs4
    AddCharset UTF-7       .utf7
    AddCharset UTF-8       .utf8
    AddCharset UTF-16      .utf16
    AddCharset UTF-16BE    .utf16be
    AddCharset UTF-16LE    .utf16le
    AddCharset UTF-32      .utf32
    AddCharset UTF-32BE    .utf32be
    AddCharset UTF-32LE    .utf32le
    AddCharset euc-cn      .euc-cn
    AddCharset euc-gb      .euc-gb
    AddCharset euc-jp      .euc-jp
    AddCharset euc-kr      .euc-kr
    #Not sure how euc-tw got in - IANA doesn't list it???
    AddCharset EUC-TW      .euc-tw
    AddCharset gb2312      .gb2312 .gb
    AddCharset iso-10646-ucs-2 .ucs-2 .iso-10646-ucs-2
    AddCharset iso-10646-ucs-4 .ucs-4 .iso-10646-ucs-4
    AddCharset shift_jis   .shift_jis .sjis

    #
    # AddHandler allows you to map certain file extensions to "handlers":
    # actions unrelated to filetype. These can be either built into the server
    # or added with the Action directive (see below)
    #
    # To use CGI scripts outside of ScriptAliased directories:
    # (You will also need to add "ExecCGI" to the "Options" directive.)
    #
    #AddHandler cgi-script .cgi

    #
    # For files that include their own HTTP headers:
    #
    #AddHandler send-as-is asis

    #
    # For server-parsed imagemap files:
    #
    #AddHandler imap-file map

    #
    # For type maps (negotiated resources):
    # (This is enabled by default to allow the Apache "It Worked" page
    #  to be distributed in multiple languages.)
    #
    AddHandler type-map var

    #
    # Filters allow you to process content before it is sent to the client.
    #
    # To parse .shtml files for server-side includes (SSI):
    # (You will also need to add "Includes" to the "Options" directive.)
    #
    AddType text/html .shtml
    AddOutputFilter INCLUDES .shtml
</IfModule>

#
# Action lets you define media types that will execute a script whenever
# a matching file is called. This eliminates the need for repeated URL
# pathnames for oft-used CGI file processors.
# Format: Action media/type /cgi-script/location
# Format: Action handler-name /cgi-script/location
#

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
# Putting this all together, we can internationalize error responses.
#
# We use Alias to redirect any /error/HTTP_<error>.html.var response to
# our collection of by-error message multi-language collections.  We use 
# includes to substitute the appropriate text.
#
# You can modify the messages' appearance without changing any of the
# default HTTP_<error>.html.var files by adding the line:
#
#   Alias /error/include/ "/your/include/path/"
#
# which allows you to create your own set of files by starting with the
# /usr/share/apache2/error/include/ files and copying them to /your/include/path/, 
# even on a per-VirtualHost basis.  The default include files will display
# your Apache version number and your ServerAdmin email address regardless
# of the setting of ServerSignature.
#
# The internationalized error documents require mod_alias, mod_include
# and mod_negotiation.  To activate them, uncomment the following 30 lines.

#    Alias /error/ "/usr/share/apache2/error/"
#
#    <Directory "/usr/share/apache2/error">
#        AllowOverride None
#        Options IncludesNoExec
#        AddOutputFilter Includes html
#        AddHandler type-map var
#        Order allow,deny
#        Allow from all
#        LanguagePriority en cs de es fr it nl sv pt-br ro
#        ForceLanguagePriority Prefer Fallback
#    </Directory>
#
#    ErrorDocument 400 /error/HTTP_BAD_REQUEST.html.var
#    ErrorDocument 401 /error/HTTP_UNAUTHORIZED.html.var
#    ErrorDocument 403 /error/HTTP_FORBIDDEN.html.var
#    ErrorDocument 404 /error/HTTP_NOT_FOUND.html.var
#    ErrorDocument 405 /error/HTTP_METHOD_NOT_ALLOWED.html.var
#    ErrorDocument 408 /error/HTTP_REQUEST_TIME_OUT.html.var
#    ErrorDocument 410 /error/HTTP_GONE.html.var
#    ErrorDocument 411 /error/HTTP_LENGTH_REQUIRED.html.var
#    ErrorDocument 412 /error/HTTP_PRECONDITION_FAILED.html.var
#    ErrorDocument 413 /error/HTTP_REQUEST_ENTITY_TOO_LARGE.html.var
#    ErrorDocument 414 /error/HTTP_REQUEST_URI_TOO_LARGE.html.var
#    ErrorDocument 415 /error/HTTP_UNSUPPORTED_MEDIA_TYPE.html.var
#    ErrorDocument 500 /error/HTTP_INTERNAL_SERVER_ERROR.html.var
#    ErrorDocument 501 /error/HTTP_NOT_IMPLEMENTED.html.var
#    ErrorDocument 502 /error/HTTP_BAD_GATEWAY.html.var
#    ErrorDocument 503 /error/HTTP_SERVICE_UNAVAILABLE.html.var
#    ErrorDocument 506 /error/HTTP_VARIANT_ALSO_VARIES.html.var

<IfModule mod_setenvif.c>
    #
    # The following directives modify normal HTTP response behavior to
    # handle known problems with browser implementations.
    #
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
    # Same deal with Apple's DAV filesystem and Gnome VFS support for DAV.
    #
    BrowserMatch "Microsoft Data Access Internet Publishing Provider" redirect-carefully
    BrowserMatch "MS FrontPage" redirect-carefully
    BrowserMatch "^WebDrive" redirect-carefully
    BrowserMatch "^WebDAVFS/1.[012]" redirect-carefully
    BrowserMatch "^gnome-vfs/1.0" redirect-carefully
    BrowserMatch "^XML Spy" redirect-carefully
    BrowserMatch "^Dreamweaver-WebDAV-SCM1" redirect-carefully
</IfModule>

#<IfModule mod_status.c>
    #
    # Allow server status reports generated by mod_status,
    # with the URL of [http://servername/server-status](http://servername/server-status)
    # Change the ".example.com" to match your domain to enable.
    #
    #<Location /server-status>
    #    SetHandler server-status
    #    Order deny,allow
    #    Deny from all
    #    Allow from .example.com
    #</Location>
#</IfModule>

#<IfModule mod_info.c>
    #
    # Allow remote server configuration reports, with the URL of
    #  [http://servername/server-info](http://servername/server-info) (requires that mod_info.c be loaded).
    # Change the ".example.com" to match your domain to enable.
    #
    #<Location /server-info>
    #    SetHandler server-info
    #    Order deny,allow
    #    Deny from all
    #    Allow from .example.com
    #</Location>
#</IfModule>

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/

I tried adding those 3 lines add the bottom and restarting apache
> AddType application/x-httpd-php .php
AddType application/x-httpd-php .php3
AddType application/x-httpd-php .phtml
but still no change. My browser still saves the files

---

### Post by atria on 2007-06-20
Place it under
```
AddType application/x-compress .Z
AddType application/x-gzip .gz .tgz
```

so it looks like
```
AddType application/x-compress .Z
AddType application/x-gzip .gz .tgz
AddType application/x-httpd-php .php
AddType application/x-httpd-php .php3
AddType application/x-httpd-php .phtml
```

and restart apache.

---

### Post by kasperbs on 2007-06-20
I did that, restarted apache, restarted my pc and it still didnt work. Thank you very much for all your help its nearly response in real time :)

Any other suggestions?

---

### Post by atria on 2007-06-20
Well.. i'm not sure why it doesn't work. Do you even have php installed properly? The php module might not be loaded correctly.

[quote=kasperbs]Thank you very much for all your help its nearly response in real time[/quote]
Welcome ;)

---

### Post by hyper_ch on 2007-06-20
Well, install apache2 and php5 and then enable the module:

```

sudo a2enmod php5

```

Nothing else should be required. For setting up advanced apache/php/email server have a look at the howtos on [http://www.howtoforge.com](http://www.howtoforge.com)

---

### Post by kasperbs on 2007-06-20
> **atria said:**
> Do you even have php installed properly? The php module might not be loaded correctly.
How can I check that? I simply followed the instructions explained [here]("http://www.supriyadisw.net/2006/12/lamp-installation-on-ubuntu")
and did what straps suggested:
> sudo apt-get install libapache2-mod-php5 && sudo /etc/init.d/apache2 restart


---

### Post by atria on 2007-06-20
You have to enable the module as mentioned above by hyper_ch.
Either use the command posted by hyper_ch, or do it manually by adding this into apache2.conf under the modules section:

```
LoadModule php5_module <location to modules directory>/libphp5.so
```

hyper_ch's method is far cleaner though, only use the method i just posted if hyper_ch's does not work.

---

### Post by kasperbs on 2007-06-20
> sudo a2enmod php5
Thanks that worked...
Only one little question, no big deal. When I go to: > [http://localhost/phpmyadmin](http://localhost/phpmyadmin) I still get the same message, that firefox wants to save a PHTML file. But if I go to > [http://localhost/phpmyadmin/index.php](http://localhost/phpmyadmin/index.php) there is no problem, it opens as it is supposed to, but can you tell me why PHTML is preferred over PHP? And notice there is no PHTML file in that directory?

---

### Post by atria on 2007-06-20
Make sure that your directory index is set to index.php instead of the .phtml file.
Look for the directoryindex section under your apache2.conf and change it to something like
```

DirectoryIndex index.php index.html

```

Glad it worked btw! ;)

---

### Post by kasperbs on 2007-06-20
> **atria said:**
> Look for the directoryindex section under your apache2.conf There is no such section? doing a "Find" in gedit on phtml doesn't return anything. It seems like .php and phtml are not even mentioned in the apache2.conf file

EDIT: Sorry about that it was a firefox thing, I just had to restart firfox and the issue was gone...

Thankyou very much for all your help again

---

### Post by scxtt on 2007-06-20
they probably aren't, by default ... just put "index.php" on the end of the line which contains "DirectoryIndex" (like atria said) ...

---

### Post by atria on 2007-06-20
My apologies, it appears that ubuntu's apache does not follow the standard apache conf format.

Browse to /etc/apache2/mods-enabled and edit dir.conf

You should see directoryindex now.

---

### Post by az on 2007-06-20
I just looked at that tutorial and I would not reccommend installing LAMP that way.

I would reccommend this:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)


Anyway, what packages do you have installed?


dpkg -l |grep apache
dpkg -l|grep mysql
dpkg -l|grep php

---

