---
title: "apt-get not working due to proxy authentication installation problems"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by rohit raj on 2007-08-29
i  have installed ntlmaps . It is probably working fine as i am able to use firefox using localhost as proxy with 5865 port . I had put   [HTML]Acquire::http::Proxy "http://127.0.0.1:5865/";[/HTML]   in proxy file 
in /etc/apt/apt.conf/  as explained in the following site [http://michaelcarden.net/blog/index.php?m=200608](http://michaelcarden.net/blog/index.php?m=200608)

After this when i try run

[HTML]sudo apt-get update

i get the following error
[HTML]Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty Release.gpg
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/multiverse Translation-en_IN
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
  407 Proxy Authentication Required
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/universe Translation-en_IN
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
  407 Proxy Authentication Required
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security Release.gpg
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty Release
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates Release
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security Release
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/multiverse Sources
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Packages
  407 Proxy Authentication Required
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Packages
  407 Proxy Authentication Required
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Sources
  407 Proxy Authentication Required
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Sources
  407 Proxy Authentication Required
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Packages
  407 Proxy Authentication Required
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Sources
  407 Proxy Authentication Required
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Packages
  407 Proxy Authentication Required
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Sources
  407 Proxy Authentication Required
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Packages
  407 Proxy Authentication Required
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Packages
  407 Proxy Authentication Required
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Packages
  407 Proxy Authentication Required
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Packages
  407 Proxy Authentication Required
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Sources
  407 Proxy Authentication Required
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Sources
  407 Proxy Authentication Required
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/multiverse Packages
  407 Proxy Authentication Required
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/universe Packages
  407 Proxy Authentication Required
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/main Packages
  407 Proxy Authentication Required
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/restricted Packages
  407 Proxy Authentication Required
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/main Sources
  407 Proxy Authentication Required
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/restricted Sources
  407 Proxy Authentication Required
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/universe Packages
  407 Proxy Authentication Required
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/universe Sources
  407 Proxy Authentication Required
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/multiverse Packages
  407 Proxy Authentication Required
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/multiverse Sources
  407 Proxy Authentication Required
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz)  407 Proxy Authentication Required
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.[/HTML]  

if i run the same command with ntlmaps stopped 
it gives the following error  rather this kind of error because /etc/init.d/ntlmaps stop command is now not working it gives the following error
[HTML]Stopping ntlmaps: kill: 80: Operation not permitted[/HTML]  

meanwhile this is the error which i got when i had port nor 1234 in proxy file of apt/apt.conf
while port nor 5865 with ntlmaps

[HTML]Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_IN
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_IN
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty Release.gpg
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Translation-en_IN
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Translation-en_IN
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Translation-en_IN
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Translation-en_IN
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Translation-en_IN
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Translation-en_IN
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates Release.gpg
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Translation-en_IN
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Translation-en_IN
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/multiverse Translation-en_IN
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/universe Translation-en_IN
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security Release.gpg
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/main Translation-en_IN
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/restricted Translation-en_IN
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/universe Translation-en_IN
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/multiverse Translation-en_IN
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_IN.bz2)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_IN.bz2)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_IN.bz2)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_IN.bz2)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_IN.bz2)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_IN.bz2)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_IN.bz2)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_IN.bz2)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/i18n/Translation-en_IN.bz2)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_IN.bz2)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_IN.bz2)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_IN.bz2)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_IN.bz2)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_IN.bz2)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_IN.bz2)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_IN.bz2)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.[/HTML]  

does this goes to show anything

---

### Post by rohit raj on 2007-08-30
Some one please help . I am able to use ntlmaps proxy in firefox , apt-get update manger is connecting to correct port but its not updating.  Meanwhile i can add that ubuntu is showing ntlmaps having broken dependencies because installation required python version less that 2.5 but i had 2.51 .I forced it to install with 

[HTML]dpkg --force-depends-version -i ntlmaps_0.9.9-4_all.deb[/HTML]
:confused:

---

### Post by rohit raj on 2007-09-01
these are the error logs that i am getting from ntlmaps when i put the logging options in server.config file. There comes several logs file one much different from other , i am posting one of them


[HTML]HTTP/1.0 407 Proxy Authentication Required

Server: squid/2.5.STABLE11

Mime-Version: 1.0

Date: Sat, 01 Sep 2007 06:17:40 GMT

Content-Type: text/html

Content-Length: 1512

Expires: Sat, 01 Sep 2007 06:17:40 GMT

X-Squid-Error: ERR_CACHE_ACCESS_DENIED 0

X-Cache: MISS from hproxy.iitm.ac.in

Proxy-Connection: close



<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<HTML><HEAD><META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=iso-8859-1">
<TITLE>ERROR: Cache Access Denied</TITLE>
<STYLE type="text/css"><!--BODY{background-color:#ffffff;font-family:verdana,sans-serif}PRE{font-family:sans-serif}--></STYLE>
</HEAD>
<BODY>
<H1>ERROR</H1>
<H2>Cache Access Denied</H2>
<HR noshade size="1px">
<P>
While trying to retrieve the URL:
<A HREF="http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz">http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz</A>
<P>
The following error was encountered:
<UL>
<LI>
<STRONG>
Cache Access Denied.
</STRONG>
</UL>
</P>

<P>Sorry, you are not currently allowed to request:
<PRE>    http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz</PRE>
from this cache until you have authenticated yourself.
</P>

<P>
You need to use Netscape version 2.0 or greater, or Microsoft Internet
Explorer 3.0, or an HTTP/1.1 compliant browser for this to work.  Please
contact the <A HREF="mailto:webmaster">cache administrator</a> if you have
difficulties authenticating yourself or 
<A HREF="http://hproxy.iitm.ac.in/cgi-bin/chpasswd.cgi">change</a> your default password.
</P>

<BR clear="all">
<HR noshade size="1px">
<ADDRESS>
Generated Sat, 01 Sep 2007 06:17:40 GMT by hproxy.iitm.ac.in (squid/2.5.STABLE11)
</ADDRESS>
</BODY></HTML>[/HTML] 


Do i need to make any changes in server .config file for apt-get to work 

[HTML]#========================================================================

[GENERAL]



LISTEN_PORT:1234



# If you want APS to authenticate you at WWW servers using NTLM then just leave this

# value blank like PARENT_PROXY: and APS will connect to web servers directly.

# You can specify more than one proxy by leaving a space between each one, and

# APS will detect when one fails and automatically fail-over to the next. EG:

#PARENT_PROXY:first_proxy second_proxy third_proxy

# And NOTE that NTLM cannot pass through another proxy server.

PARENT_PROXY:hproxy.iitm.ac.in



PARENT_PROXY_PORT:3128



# APS will poll the upstream proxy and attempt to fail-over to a new one if it doesn't

# get a response within an appropriate time frame.  The amount of time that it will

# wait for a response before attempting fail-over is specified, in seconds, below:

PARENT_PROXY_TIMEOUT:15



# Set to 1 if you want to grant this authorization service to clients from other computers.

# NOTE: all the users from other hosts that will be using you copy of APS for authentication

# will be using your credentials in NTLM auth at the remote host.

ALLOW_EXTERNAL_CLIENTS:0



# If you want to allow some other but not all computers to use your proxy for authorization,

# just set ALLOW_EXTERNAL_CLIENTS:0 and put friendly IP addresses here.

# Use space as a delimiter.

# NOTE that special addesses don't work here (192.168.3.0 for example).

FRIENDLY_IPS:



# Requested URLs are written to "url.log" file. May be useful.

URL_LOG:1



# When a network service listens for connections, there is a maximum number of connection

# attempts to that service that the underlying OS will allow to backlog waiting for a response

# before the OS will start dropping new connection attempts with 'Connection refused'.  The

# standard method of determining the maximum number of backlogged connections is to use the

# SOMAXCONN constant, which is supposed to represent the maximum number that an OS will support

# (for example, 5 on Windows 2000 Pro, and 200 on Windows 2000 server).  However, because this

# is a statically compiled value in a Python distribution, usually this instead represents the

# the most conservative value (5 on all Windows platforms, and 128 on the GNU/Linux variant I

# tried).  So if you are running (for example) a massively threaded/parallel download manager,

# the default value of, say, 5, or whatever SOMAXCONN happens to be set to, may be too low and

# cause some connections to fail.  The value below can be set to any integer (it seems that

# Python just silently caps values above the hard limit for the underlying platform), or it can

# be set to the special value of SOMAXCONN (i.e. MAX_CONNECTION_BACKLOG:SOMAXCONN), to use

# whatever this value happens to be set to in your Python build.  Setting this higher than

# necessary may cause APS to consume more memory than you needed to.

MAX_CONNECTION_BACKLOG:5



#========================================================================

[CLIENT_HEADER]



# This section describes what and how the server should change in the clients headers.

# Made in order to prevent parent proxy from seeing that you are using wget instead of IE5.5



Accept: image/gif, image/x-xbitmap, image/jpeg, image/pjpeg, application/vnd.ms-excel, application/msword, application/vnd.ms-powerpoint, */*

User-Agent: Mozilla/4.0 (compatible; MSIE 5.5; Windows 98)



# for windows 2000 emulation ;)

# User-Agent: Mozilla/4.0 (compatible; MSIE 5.5; Windows NT5)




#========================================================================

[NTLM_AUTH]



# Optional value, if leaved blank then APS will use gethostname() to determine

# host's name.

# NOTE1: If you Linux host name differs from Windows host name then it may be that

#        MS server wont recognize you host at all and wont grant you access

#        to resources requested. Then you have to use this option and APS will use

#        this name in NTLM negotiations.

# NOTE2: There are several reports that you can successfully use "foreign" host name

#        here. Say, if user may access a resource from 'host1' and may not from 'host2'

#        then there is a chance that APS running on 'host2' with NT_HOSTNAME:host1 will

#        be able to be granted access to the restricted resource. However use this on

#        you own risk as such a trick may be considered as a hack or something.

NT_HOSTNAME:



# Windows Domain.

# NOTE: it is not full qualified internet domain, but windows network domain.

NT_DOMAIN:iitm



# What user's name to use during authorization. It may differ form real current username.

# If you enable NTLM_TO_BASIC, below, you can either leave this blank or simply

# hash it out.

USER:ee04b046



# Password. Just leave it blank here and server will request it at the start time,

# or, if you enable NTLM_TO_BASIC, below, you can either leave this blank or simply

# hash it out, and you *won't* be prompted for a password at start time.

PASSWORD:******



# These two options replace old FULL_NTLM option.

# NTLM authentication consists virtually of two parts: LM and NT. Windows95/98 use

# only LM part, WindowsNT/2000 can use NT and LM or just NT part.

# Almost always using just LM part will be enough. I had several reports

# about LM and NT requirement and no about just NT.

# So try to setup 1, 1 only if you have enough reasons to do so and when you understand

# what you are doing.

# 0, 0 is an illegal combination

# NOTE: if you change these options then you have to setup flag option accordingly.

LM_PART:1

NT_PART:0



# Highly experimental option. See research.txt for details.

# LM - 06820000

# NT - 05820000

# LM + NT - 07820000

NTLM_FLAGS: 06820000



# This option makes APS try to translate NTLM authentication to very usual "Basic"

# scheme. Almost all http clients know it. With this option set to 1 user will be requested

# by his browser to enter his credentials and these username and password will be used by

# APS for NTLM authentication at MS Proxy server or Web server.

# In such a case different users can use one runnig APS with their own credentials.

# NOTE1: currently translation works so it allows only one try for entering

#        username/password. If you make a mistake you will have to restart you browser.

# NOTE2: With debug:1 basic username/password will be written in log file in clear

#        text format. I could try hide it, but the basic scheme is so weak that anybody

#        who had access to APS would be able to get it.

NTLM_TO_BASIC:0



#========================================================================

[DEBUG]



# Set this to 1 if you want to see debug info in many log files. One per connection.

DEBUG:1



# Set this to 1 to get even more debug info.

BIN_DEBUG:1



# Set this to 1 to see some strange activity on screen. Actually you won't want it.

SCR_DEBUG:0



# Not actually a debug option but gives you some details on authentication process

# into *.auth logs. Also see research.txt.

AUTH_DEBUG:1


[/HTML]

---

### Post by rohit raj on 2007-09-03
Somebody please help   :(

 At least can anyone tell does ubuntu 7.04 does properly support intel 915g chipset . I mean natively , i don' t want to go through another  load of craps (after this issue ever gets sorted out )for getting my sound card to work . I have been waiting on crap mandriva 2006 for years for my sound to work

Or at the very least is there any simple way to get sound working on my computer before getting that apt-get issue sorted out

---

### Post by jorno on 2007-09-10
I don't know if anyone still has this problem, but I found my solution in another post.

The steps mentioned here earlier are good and all, BUT if those of  you who's got this problem is in a Windows environment with a Microsoft ISA Proxy that need authentication, this is the solution that worked for me:

You need to install NTLMAPS.

[http://packages.ubuntu.com/feisty/web/ntlmaps](http://packages.ubuntu.com/feisty/web/ntlmaps)
* Go there, and download, either from within Firefox (if you manage to get Proxy working with Firefox - I did, but not apt-get or Synaptics or anything else).
* Download the package for ntlmaps (this is for Ubuntu Feisty)
* Start a terminal, find your downloaded package, and type:
*sudo dpkg -i ntlmaps_0.9.9.0.1-6_all.deb*
This should guide you trough the installation of the package...

BUT, my problems didn't stop there!
After, I had to edit /etc/ntlmaps/server.cfg manually.
( *sudo vim /etc /ntlmaps/server.cfg* )
Then I saw that the config-file was formatted with DOS (not UNIX), so I had to tell vim to convert it to UNIX-format. Do this in vim:
*:set fileformat=unix*
*:wq*
This should convert the file, and save it.
I also had to change some of the options:
Under the [CLIENT_HEADER] section, I had to comment out the first Accept and User-Agent part (Windows 98), and then uncomment the next part (Windows 2000 emulation).
Then I filled in "NT_HOSTNAME" (remembered what PC number this workstation had in Windows), and "NT_DOMAIN").

After those changes, restart ntlmaps:
*/etc/init.d/ntlmaps restart*

And point all your proxy-settings to: [http://127.0.0.1:5865](http://127.0.0.1:5865)

Make a file: */etc/apt/apt.conf*
Acquire::http::Proxy "http://127.0.0.1:5865";

And then try "*apt-get update*".

You could also insert this into:
System -> Preferences -> Network Proxy

And in Synaptics:
System -> Administration -> Synaptics -> Settings -> Preferences -> Network:
Manual proxy configuration:

127.0.0.1 port 5865 (no authentication)


This should do the trick! It did for me.. Please ask if there is something not clear yet, or if I should correct any of this. (Sorry, English is not my native tongue).

---

