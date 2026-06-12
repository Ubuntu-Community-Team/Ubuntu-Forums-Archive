---
title: "A good download manager"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by O-pos on 2007-07-04
Hello,

Could someone recommend to me a good professional flexible download manager? I almost prefer CLI mode, but GUI would be ok too.

---

### Post by ramjet_1953 on 2007-07-04
I use MultiGet and it works really well.

[http://multiget.sourceforge.net/](http://multiget.sourceforge.net/)

There is a deb package here to download.

Regards,
Roger :cool:

---

### Post by alienexplorers on 2007-07-04
If you are running Firefox then DownThemAll! is a nice download manager.

---

### Post by kevinlyfellow on 2007-07-04
hmmm, wget?

Well, a good gui one is d4x

---

### Post by swisscow on 2007-07-04
With Konqueror, KGET seems to do the job

---

### Post by hyper_ch on 2007-07-04
d4x is quite nice

---

### Post by O-pos on 2007-07-04
Thank you for replies.

What about wget? seems to be wery powerful and robust. Does it have multiple streams support?

---

### Post by ltk5 on 2007-07-04
These are all the options it has :D
```
Startup:
  -V,  --version           display the version of Wget and exit.
  -h,  --help              print this help.
  -b,  --background        go to background after startup.
  -e,  --execute=COMMAND   execute a `.wgetrc'-style command.

Logging and input file:
  -o,  --output-file=FILE    log messages to FILE.
  -a,  --append-output=FILE  append messages to FILE.
  -d,  --debug               print lots of debugging information.
  -q,  --quiet               quiet (no output).
  -v,  --verbose             be verbose (this is the default).
  -nv, --no-verbose          turn off verboseness, without being quiet.
  -i,  --input-file=FILE     download URLs found in FILE.
  -F,  --force-html          treat input file as HTML.
  -B,  --base=URL            prefixs URL to relative links in -F -i file.

Download:
  -t,  --tries=NUMBER            set number of retries to NUMBER (0 unlimits).
       --retry-connrefused       retry even if connection is refused.
  -O,  --output-document=FILE    write documents to FILE.
  -nc, --no-clobber              skip downloads that would download to
                                 existing files.
  -c,  --continue                resume getting a partially-downloaded file.
       --progress=TYPE           select progress gauge type.
  -N,  --timestamping            don't re-retrieve files unless newer than
                                 local.
  -S,  --server-response         print server response.
       --spider                  don't download anything.
  -T,  --timeout=SECONDS         set all timeout values to SECONDS.
       --dns-timeout=SECS        set the DNS lookup timeout to SECS.
       --connect-timeout=SECS    set the connect timeout to SECS.
       --read-timeout=SECS       set the read timeout to SECS.
  -w,  --wait=SECONDS            wait SECONDS between retrievals.
       --waitretry=SECONDS       wait 1..SECONDS between retries of a retrieval.
       --random-wait             wait from 0...2*WAIT secs between retrievals.
  -Y,  --proxy                   explicitly turn on proxy.
       --no-proxy                explicitly turn off proxy.
  -Q,  --quota=NUMBER            set retrieval quota to NUMBER.
       --bind-address=ADDRESS    bind to ADDRESS (hostname or IP) on local host.
       --limit-rate=RATE         limit download rate to RATE.
       --no-dns-cache            disable caching DNS lookups.
       --restrict-file-names=OS  restrict chars in file names to ones OS allows.
  -4,  --inet4-only              connect only to IPv4 addresses.
  -6,  --inet6-only              connect only to IPv6 addresses.
       --prefer-family=FAMILY    connect first to addresses of specified family,
                                 one of IPv6, IPv4, or none.
       --user=USER               set both ftp and http user to USER.
       --password=PASS           set both ftp and http password to PASS.

Directories:
  -nd, --no-directories           don't create directories.
  -x,  --force-directories        force creation of directories.
  -nH, --no-host-directories      don't create host directories.
       --protocol-directories     use protocol name in directories.
  -P,  --directory-prefix=PREFIX  save files to PREFIX/...
       --cut-dirs=NUMBER          ignore NUMBER remote directory components.

HTTP options:
       --http-user=USER        set http user to USER.
       --http-password=PASS    set http password to PASS.
       --no-cache              disallow server-cached data.
  -E,  --html-extension        save HTML documents with `.html' extension.
       --ignore-length         ignore `Content-Length' header field.
       --header=STRING         insert STRING among the headers.
       --proxy-user=USER       set USER as proxy username.
       --proxy-password=PASS   set PASS as proxy password.
       --referer=URL           include `Referer: URL' header in HTTP request.
       --save-headers          save the HTTP headers to file.
  -U,  --user-agent=AGENT      identify as AGENT instead of Wget/VERSION.
       --no-http-keep-alive    disable HTTP keep-alive (persistent connections).
       --no-cookies            don't use cookies.
       --load-cookies=FILE     load cookies from FILE before session.
       --save-cookies=FILE     save cookies to FILE after session.
       --keep-session-cookies  load and save session (non-permanent) cookies.
       --post-data=STRING      use the POST method; send STRING as the data.
       --post-file=FILE        use the POST method; send contents of FILE.

HTTPS (SSL/TLS) options:
       --secure-protocol=PR     choose secure protocol, one of auto, SSLv2,
                                SSLv3, and TLSv1.
       --no-check-certificate   don't validate the server's certificate.
       --certificate=FILE       client certificate file.
       --certificate-type=TYPE  client certificate type, PEM or DER.
       --private-key=FILE       private key file.
       --private-key-type=TYPE  private key type, PEM or DER.
       --ca-certificate=FILE    file with the bundle of CA's.
       --ca-directory=DIR       directory where hash list of CA's is stored.
       --random-file=FILE       file with random data for seeding the SSL PRNG.
       --egd-file=FILE          file naming the EGD socket with random data.

FTP options:
       --ftp-user=USER         set ftp user to USER.
       --ftp-password=PASS     set ftp password to PASS.
       --no-remove-listing     don't remove `.listing' files.
       --no-glob               turn off FTP file name globbing.
       --no-passive-ftp        disable the "passive" transfer mode.
       --retr-symlinks         when recursing, get linked-to files (not dir).
       --preserve-permissions  preserve remote file permissions.

Recursive download:
  -r,  --recursive          specify recursive download.
  -l,  --level=NUMBER       maximum recursion depth (inf or 0 for infinite).
       --delete-after       delete files locally after downloading them.
  -k,  --convert-links      make links in downloaded HTML point to local files.
  -K,  --backup-converted   before converting file X, back up as X.orig.
  -m,  --mirror             shortcut for -N -r -l inf --no-remove-listing.
  -p,  --page-requisites    get all images, etc. needed to display HTML page.
       --strict-comments    turn on strict (SGML) handling of HTML comments.

Recursive accept/reject:
  -A,  --accept=LIST               comma-separated list of accepted extensions.
  -R,  --reject=LIST               comma-separated list of rejected extensions.
  -D,  --domains=LIST              comma-separated list of accepted domains.
       --exclude-domains=LIST      comma-separated list of rejected domains.
       --follow-ftp                follow FTP links from HTML documents.
       --follow-tags=LIST          comma-separated list of followed HTML tags.
       --ignore-tags=LIST          comma-separated list of ignored HTML tags.
  -H,  --span-hosts                go to foreign hosts when recursive.
  -L,  --relative                  follow relative links only.
  -I,  --include-directories=LIST  list of allowed directories.
  -X,  --exclude-directories=LIST  list of excluded directories.
  -np, --no-parent                 don't ascend to the parent directory.

```

---

### Post by lbelloq on 2007-07-04
d4x works very well... something I miss from it is an option to minimize to tray.

---

### Post by hyper_ch on 2007-07-04
What do you have different desktops for? ;

---

### Post by lbelloq on 2007-07-04
Then how can I minimize d4x to tray instead of using space in the taskbar?

---

### Post by O-pos on 2007-07-04
There was nothing regarding breakdown in multiple streams. Does wget lack this feature? Then I think I should try d4x.

> **ltk5 said:**
> These are all the options it has :D
```
Startup:
  -V,  --version           display the version of Wget and exit.
  -h,  --help              print this help.
  -b,  --background        go to background after startup.
  -e,  --execute=COMMAND   execute a `.wgetrc'-style command.

Logging and input file:
  -o,  --output-file=FILE    log messages to FILE.
  -a,  --append-output=FILE  append messages to FILE.
  -d,  --debug               print lots of debugging information.
  -q,  --quiet               quiet (no output).
  -v,  --verbose             be verbose (this is the default).
  -nv, --no-verbose          turn off verboseness, without being quiet.
  -i,  --input-file=FILE     download URLs found in FILE.
  -F,  --force-html          treat input file as HTML.
  -B,  --base=URL            prefixs URL to relative links in -F -i file.

Download:
  -t,  --tries=NUMBER            set number of retries to NUMBER (0 unlimits).
       --retry-connrefused       retry even if connection is refused.
  -O,  --output-document=FILE    write documents to FILE.
  -nc, --no-clobber              skip downloads that would download to
                                 existing files.
  -c,  --continue                resume getting a partially-downloaded file.
       --progress=TYPE           select progress gauge type.
  -N,  --timestamping            don't re-retrieve files unless newer than
                                 local.
  -S,  --server-response         print server response.
       --spider                  don't download anything.
  -T,  --timeout=SECONDS         set all timeout values to SECONDS.
       --dns-timeout=SECS        set the DNS lookup timeout to SECS.
       --connect-timeout=SECS    set the connect timeout to SECS.
       --read-timeout=SECS       set the read timeout to SECS.
  -w,  --wait=SECONDS            wait SECONDS between retrievals.
       --waitretry=SECONDS       wait 1..SECONDS between retries of a retrieval.
       --random-wait             wait from 0...2*WAIT secs between retrievals.
  -Y,  --proxy                   explicitly turn on proxy.
       --no-proxy                explicitly turn off proxy.
  -Q,  --quota=NUMBER            set retrieval quota to NUMBER.
       --bind-address=ADDRESS    bind to ADDRESS (hostname or IP) on local host.
       --limit-rate=RATE         limit download rate to RATE.
       --no-dns-cache            disable caching DNS lookups.
       --restrict-file-names=OS  restrict chars in file names to ones OS allows.
  -4,  --inet4-only              connect only to IPv4 addresses.
  -6,  --inet6-only              connect only to IPv6 addresses.
       --prefer-family=FAMILY    connect first to addresses of specified family,
                                 one of IPv6, IPv4, or none.
       --user=USER               set both ftp and http user to USER.
       --password=PASS           set both ftp and http password to PASS.

Directories:
  -nd, --no-directories           don't create directories.
  -x,  --force-directories        force creation of directories.
  -nH, --no-host-directories      don't create host directories.
       --protocol-directories     use protocol name in directories.
  -P,  --directory-prefix=PREFIX  save files to PREFIX/...
       --cut-dirs=NUMBER          ignore NUMBER remote directory components.

HTTP options:
       --http-user=USER        set http user to USER.
       --http-password=PASS    set http password to PASS.
       --no-cache              disallow server-cached data.
  -E,  --html-extension        save HTML documents with `.html' extension.
       --ignore-length         ignore `Content-Length' header field.
       --header=STRING         insert STRING among the headers.
       --proxy-user=USER       set USER as proxy username.
       --proxy-password=PASS   set PASS as proxy password.
       --referer=URL           include `Referer: URL' header in HTTP request.
       --save-headers          save the HTTP headers to file.
  -U,  --user-agent=AGENT      identify as AGENT instead of Wget/VERSION.
       --no-http-keep-alive    disable HTTP keep-alive (persistent connections).
       --no-cookies            don't use cookies.
       --load-cookies=FILE     load cookies from FILE before session.
       --save-cookies=FILE     save cookies to FILE after session.
       --keep-session-cookies  load and save session (non-permanent) cookies.
       --post-data=STRING      use the POST method; send STRING as the data.
       --post-file=FILE        use the POST method; send contents of FILE.

HTTPS (SSL/TLS) options:
       --secure-protocol=PR     choose secure protocol, one of auto, SSLv2,
                                SSLv3, and TLSv1.
       --no-check-certificate   don't validate the server's certificate.
       --certificate=FILE       client certificate file.
       --certificate-type=TYPE  client certificate type, PEM or DER.
       --private-key=FILE       private key file.
       --private-key-type=TYPE  private key type, PEM or DER.
       --ca-certificate=FILE    file with the bundle of CA's.
       --ca-directory=DIR       directory where hash list of CA's is stored.
       --random-file=FILE       file with random data for seeding the SSL PRNG.
       --egd-file=FILE          file naming the EGD socket with random data.

FTP options:
       --ftp-user=USER         set ftp user to USER.
       --ftp-password=PASS     set ftp password to PASS.
       --no-remove-listing     don't remove `.listing' files.
       --no-glob               turn off FTP file name globbing.
       --no-passive-ftp        disable the "passive" transfer mode.
       --retr-symlinks         when recursing, get linked-to files (not dir).
       --preserve-permissions  preserve remote file permissions.

Recursive download:
  -r,  --recursive          specify recursive download.
  -l,  --level=NUMBER       maximum recursion depth (inf or 0 for infinite).
       --delete-after       delete files locally after downloading them.
  -k,  --convert-links      make links in downloaded HTML point to local files.
  -K,  --backup-converted   before converting file X, back up as X.orig.
  -m,  --mirror             shortcut for -N -r -l inf --no-remove-listing.
  -p,  --page-requisites    get all images, etc. needed to display HTML page.
       --strict-comments    turn on strict (SGML) handling of HTML comments.

Recursive accept/reject:
  -A,  --accept=LIST               comma-separated list of accepted extensions.
  -R,  --reject=LIST               comma-separated list of rejected extensions.
  -D,  --domains=LIST              comma-separated list of accepted domains.
       --exclude-domains=LIST      comma-separated list of rejected domains.
       --follow-ftp                follow FTP links from HTML documents.
       --follow-tags=LIST          comma-separated list of followed HTML tags.
       --ignore-tags=LIST          comma-separated list of ignored HTML tags.
  -H,  --span-hosts                go to foreign hosts when recursive.
  -L,  --relative                  follow relative links only.
  -I,  --include-directories=LIST  list of allowed directories.
  -X,  --exclude-directories=LIST  list of excluded directories.
  -np, --no-parent                 don't ascend to the parent directory.

```

---

### Post by vexorian on 2007-07-04
gwget does the job for me.

I am not sure what is a 'professional' download manager...

---

### Post by O-pos on 2007-07-04
> **vexorian said:**
> gwget does the job for me.

I am not sure what is a 'professional' download manager...

Under "professional" I meant that it is compliant, configurable and can deal with complicated tasks.

---

### Post by kevinlyfellow on 2007-07-04
> **lbelloq said:**
> Then how can I minimize d4x to tray instead of using space in the taskbar?

d4x shows up in my notification area when its running.  If I want it hidden, I just double click the icon in the notification area.

---

### Post by lbelloq on 2007-07-04
Thanks. ^^

---

### Post by vexorian on 2007-07-04
> **O-pos said:**
> Under "professional" I meant that it is compliant, configurable and can deal with complicated tasks.
That answers one question but pops out some new questions:

a) Compliant to what?
b) what kind of complicated tasks? I mean, how can I improve my downloading experience?


> 
Then how can I minimize d4x to tray instead of using space in the taskbar?what I like of Linux desktops is that when something is using undesirable taskbar space, I just move it to another desktop...

---

### Post by O-pos on 2007-07-13
I got a link 
```

wget http://www.rustavi2.com/news/video_progs.php?id_clip=475

```

It leads to a video file, which I want to download with wget. however, when I just type
```

wget http://www.rustavi2.com/news/video_progs.php?id_clip=475

```
it does not download a video, but a small stupid file instead. I know there is option for that, but couldn't find below. Can anyone tell me what is the command to follow that link and get the video?

Thanks
> **ltk5 said:**
> These are all the options it has :D
```
Startup:
  -V,  --version           display the version of Wget and exit.
  -h,  --help              print this help.
  -b,  --background        go to background after startup.
  -e,  --execute=COMMAND   execute a `.wgetrc'-style command.

Logging and input file:
  -o,  --output-file=FILE    log messages to FILE.
  -a,  --append-output=FILE  append messages to FILE.
  -d,  --debug               print lots of debugging information.
  -q,  --quiet               quiet (no output).
  -v,  --verbose             be verbose (this is the default).
  -nv, --no-verbose          turn off verboseness, without being quiet.
  -i,  --input-file=FILE     download URLs found in FILE.
  -F,  --force-html          treat input file as HTML.
  -B,  --base=URL            prefixs URL to relative links in -F -i file.

Download:
  -t,  --tries=NUMBER            set number of retries to NUMBER (0 unlimits).
       --retry-connrefused       retry even if connection is refused.
  -O,  --output-document=FILE    write documents to FILE.
  -nc, --no-clobber              skip downloads that would download to
                                 existing files.
  -c,  --continue                resume getting a partially-downloaded file.
       --progress=TYPE           select progress gauge type.
  -N,  --timestamping            don't re-retrieve files unless newer than
                                 local.
  -S,  --server-response         print server response.
       --spider                  don't download anything.
  -T,  --timeout=SECONDS         set all timeout values to SECONDS.
       --dns-timeout=SECS        set the DNS lookup timeout to SECS.
       --connect-timeout=SECS    set the connect timeout to SECS.
       --read-timeout=SECS       set the read timeout to SECS.
  -w,  --wait=SECONDS            wait SECONDS between retrievals.
       --waitretry=SECONDS       wait 1..SECONDS between retries of a retrieval.
       --random-wait             wait from 0...2*WAIT secs between retrievals.
  -Y,  --proxy                   explicitly turn on proxy.
       --no-proxy                explicitly turn off proxy.
  -Q,  --quota=NUMBER            set retrieval quota to NUMBER.
       --bind-address=ADDRESS    bind to ADDRESS (hostname or IP) on local host.
       --limit-rate=RATE         limit download rate to RATE.
       --no-dns-cache            disable caching DNS lookups.
       --restrict-file-names=OS  restrict chars in file names to ones OS allows.
  -4,  --inet4-only              connect only to IPv4 addresses.
  -6,  --inet6-only              connect only to IPv6 addresses.
       --prefer-family=FAMILY    connect first to addresses of specified family,
                                 one of IPv6, IPv4, or none.
       --user=USER               set both ftp and http user to USER.
       --password=PASS           set both ftp and http password to PASS.

Directories:
  -nd, --no-directories           don't create directories.
  -x,  --force-directories        force creation of directories.
  -nH, --no-host-directories      don't create host directories.
       --protocol-directories     use protocol name in directories.
  -P,  --directory-prefix=PREFIX  save files to PREFIX/...
       --cut-dirs=NUMBER          ignore NUMBER remote directory components.

HTTP options:
       --http-user=USER        set http user to USER.
       --http-password=PASS    set http password to PASS.
       --no-cache              disallow server-cached data.
  -E,  --html-extension        save HTML documents with `.html' extension.
       --ignore-length         ignore `Content-Length' header field.
       --header=STRING         insert STRING among the headers.
       --proxy-user=USER       set USER as proxy username.
       --proxy-password=PASS   set PASS as proxy password.
       --referer=URL           include `Referer: URL' header in HTTP request.
       --save-headers          save the HTTP headers to file.
  -U,  --user-agent=AGENT      identify as AGENT instead of Wget/VERSION.
       --no-http-keep-alive    disable HTTP keep-alive (persistent connections).
       --no-cookies            don't use cookies.
       --load-cookies=FILE     load cookies from FILE before session.
       --save-cookies=FILE     save cookies to FILE after session.
       --keep-session-cookies  load and save session (non-permanent) cookies.
       --post-data=STRING      use the POST method; send STRING as the data.
       --post-file=FILE        use the POST method; send contents of FILE.

HTTPS (SSL/TLS) options:
       --secure-protocol=PR     choose secure protocol, one of auto, SSLv2,
                                SSLv3, and TLSv1.
       --no-check-certificate   don't validate the server's certificate.
       --certificate=FILE       client certificate file.
       --certificate-type=TYPE  client certificate type, PEM or DER.
       --private-key=FILE       private key file.
       --private-key-type=TYPE  private key type, PEM or DER.
       --ca-certificate=FILE    file with the bundle of CA's.
       --ca-directory=DIR       directory where hash list of CA's is stored.
       --random-file=FILE       file with random data for seeding the SSL PRNG.
       --egd-file=FILE          file naming the EGD socket with random data.

FTP options:
       --ftp-user=USER         set ftp user to USER.
       --ftp-password=PASS     set ftp password to PASS.
       --no-remove-listing     don't remove `.listing' files.
       --no-glob               turn off FTP file name globbing.
       --no-passive-ftp        disable the "passive" transfer mode.
       --retr-symlinks         when recursing, get linked-to files (not dir).
       --preserve-permissions  preserve remote file permissions.

Recursive download:
  -r,  --recursive          specify recursive download.
  -l,  --level=NUMBER       maximum recursion depth (inf or 0 for infinite).
       --delete-after       delete files locally after downloading them.
  -k,  --convert-links      make links in downloaded HTML point to local files.
  -K,  --backup-converted   before converting file X, back up as X.orig.
  -m,  --mirror             shortcut for -N -r -l inf --no-remove-listing.
  -p,  --page-requisites    get all images, etc. needed to display HTML page.
       --strict-comments    turn on strict (SGML) handling of HTML comments.

Recursive accept/reject:
  -A,  --accept=LIST               comma-separated list of accepted extensions.
  -R,  --reject=LIST               comma-separated list of rejected extensions.
  -D,  --domains=LIST              comma-separated list of accepted domains.
       --exclude-domains=LIST      comma-separated list of rejected domains.
       --follow-ftp                follow FTP links from HTML documents.
       --follow-tags=LIST          comma-separated list of followed HTML tags.
       --ignore-tags=LIST          comma-separated list of ignored HTML tags.
  -H,  --span-hosts                go to foreign hosts when recursive.
  -L,  --relative                  follow relative links only.
  -I,  --include-directories=LIST  list of allowed directories.
  -X,  --exclude-directories=LIST  list of excluded directories.
  -np, --no-parent                 don't ascend to the parent directory.

```

---

