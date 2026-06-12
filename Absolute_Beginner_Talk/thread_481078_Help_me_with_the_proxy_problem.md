---
title: "Help me with the proxy problem"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by TerryChou on 2007-06-22
Hello, everyone,

I got a proxy problem here:
I set up the system Network Proxy to a server, but when I run "sudo apt-get update", it doesn't work. 
The system shows me:
> Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg                                                                  
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release.gpg                                                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg                                                        
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty/main Translation-en_US                                
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty/restricted Translation-en_US                                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US                                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US                            
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty/universe Translation-en_US                                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US                                            
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Translation-en_US                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US                              
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release                   
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty/multiverse Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release               
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Packages                                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release                                                 
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-updates Release.gpg                                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages                                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages                                                                           
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-updates/main Translation-en_US                                                                       
Err [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Packages             
  407 Unauthorized
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages             
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages   
  407 Unauthorized
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-updates/restricted Translation-en_US
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-updates/universe Translation-en_US
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages               
  407 Unauthorized
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
  407 Unauthorized
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-security Release.gpg             
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages                 
  407 Unauthorized
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-security/main Translation-en_US
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-security/restricted Translation-en_US
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-security/universe Translation-en_US
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-security/multiverse Translation-en_US
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty Release    
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-updates Release
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-security Release
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty/main Packages
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty/restricted Packages
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty/main Sources
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty/restricted Sources
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty/universe Packages
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty/universe Sources
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty/multiverse Packages
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty/multiverse Sources
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-updates/main Packages
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-updates/restricted Packages
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-updates/main Sources
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-updates/restricted Sources
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-updates/universe Packages
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-security/main Packages
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-security/restricted Packages
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-security/main Sources
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-security/restricted Sources
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-security/universe Packages
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-security/universe Sources
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-security/multiverse Packages
Ign [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-security/multiverse Sources
Err [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty/main Packages
  407 Unauthorized
Err [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty/restricted Packages
  407 Unauthorized
Err [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty/main Sources
  407 Unauthorized
Err [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty/restricted Sources
  407 Unauthorized
Err [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty/universe Packages
  407 Unauthorized
Err [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty/universe Sources
  407 Unauthorized
Err [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty/multiverse Packages
  407 Unauthorized
Err [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty/multiverse Sources
  407 Unauthorized
Err [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-updates/main Packages
  407 Unauthorized
Err [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-updates/restricted Packages
  407 Unauthorized
Err [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-updates/main Sources
  407 Unauthorized
Err [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-updates/restricted Sources
  407 Unauthorized
Err [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-updates/universe Packages
  407 Unauthorized
Err [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-security/main Packages
  407 Unauthorized
Err [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-security/restricted Packages
  407 Unauthorized
Err [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-security/main Sources
  407 Unauthorized
Err [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-security/restricted Sources
  407 Unauthorized
Err [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-security/universe Packages
  407 Unauthorized
Err [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-security/universe Sources
  407 Unauthorized
Err [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-security/multiverse Packages
  407 Unauthorized
Err [http://debian.linux.org.tw](http://debian.linux.org.tw) feisty-security/multiverse Sources
  407 Unauthorized
Failed to fetch [http://ubuntu.beryl-project.org/dists/feisty/main/binary-i386/Packages.gz](http://ubuntu.beryl-project.org/dists/feisty/main/binary-i386/Packages.gz)  407 Unauthorized
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz)  407 Unauthorized
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz)  407 Unauthorized
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz)  407 Unauthorized
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  407 Unauthorized
Failed to fetch [http://debian.linux.org.tw/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://debian.linux.org.tw/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  407 Unauthorized
Failed to fetch [http://debian.linux.org.tw/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://debian.linux.org.tw/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz)  407 Unauthorized
Failed to fetch [http://debian.linux.org.tw/ubuntu/dists/feisty/main/source/Sources.gz](http://debian.linux.org.tw/ubuntu/dists/feisty/main/source/Sources.gz)  407 Unauthorized
Failed to fetch [http://debian.linux.org.tw/ubuntu/dists/feisty/restricted/source/Sources.gz](http://debian.linux.org.tw/ubuntu/dists/feisty/restricted/source/Sources.gz)  407 Unauthorized
Failed to fetch [http://debian.linux.org.tw/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://debian.linux.org.tw/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  407 Unauthorized
Failed to fetch [http://debian.linux.org.tw/ubuntu/dists/feisty/universe/source/Sources.gz](http://debian.linux.org.tw/ubuntu/dists/feisty/universe/source/Sources.gz)  407 Unauthorized
Failed to fetch [http://debian.linux.org.tw/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://debian.linux.org.tw/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz)  407 Unauthorized
Failed to fetch [http://debian.linux.org.tw/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://debian.linux.org.tw/ubuntu/dists/feisty/multiverse/source/Sources.gz)  407 Unauthorized
Failed to fetch [http://debian.linux.org.tw/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz](http://debian.linux.org.tw/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz)  407 Unauthorized
Failed to fetch [http://debian.linux.org.tw/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz](http://debian.linux.org.tw/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz)  407 Unauthorized
Failed to fetch [http://debian.linux.org.tw/ubuntu/dists/feisty-updates/main/source/Sources.gz](http://debian.linux.org.tw/ubuntu/dists/feisty-updates/main/source/Sources.gz)  407 Unauthorized
Failed to fetch [http://debian.linux.org.tw/ubuntu/dists/feisty-updates/restricted/source/Sources.gz](http://debian.linux.org.tw/ubuntu/dists/feisty-updates/restricted/source/Sources.gz)  407 Unauthorized
Failed to fetch [http://debian.linux.org.tw/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz](http://debian.linux.org.tw/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz)  407 Unauthorized
Failed to fetch [http://debian.linux.org.tw/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz](http://debian.linux.org.tw/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz)  407 Unauthorized
Failed to fetch [http://debian.linux.org.tw/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz](http://debian.linux.org.tw/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz)  407 Unauthorized
Failed to fetch [http://debian.linux.org.tw/ubuntu/dists/feisty-security/main/source/Sources.gz](http://debian.linux.org.tw/ubuntu/dists/feisty-security/main/source/Sources.gz)  407 Unauthorized
Failed to fetch [http://debian.linux.org.tw/ubuntu/dists/feisty-security/restricted/source/Sources.gz](http://debian.linux.org.tw/ubuntu/dists/feisty-security/restricted/source/Sources.gz)  407 Unauthorized
Failed to fetch [http://debian.linux.org.tw/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz](http://debian.linux.org.tw/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz)  407 Unauthorized
Failed to fetch [http://debian.linux.org.tw/ubuntu/dists/feisty-security/universe/source/Sources.gz](http://debian.linux.org.tw/ubuntu/dists/feisty-security/universe/source/Sources.gz)  407 Unauthorized
Failed to fetch [http://debian.linux.org.tw/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz](http://debian.linux.org.tw/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz)  407 Unauthorized
Failed to fetch [http://debian.linux.org.tw/ubuntu/dists/feisty-security/multiverse/source/Sources.gz](http://debian.linux.org.tw/ubuntu/dists/feisty-security/multiverse/source/Sources.gz)  407 Unauthorized
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


It is really wired because I can surf webpages by setting the Firefox proxy to the same server.
What is the problem? Does the system Network Proxy never work?
Any help will be appreciated very much!

---

### Post by wormser on 2007-06-22
try this:  System> Preferences> Network Proxy and put your settings in.

---

### Post by TerryChou on 2007-06-22
Unfortunately, It is just what I did.:(

---

### Post by wormser on 2007-06-22
try doing a ping test.

Update:
I found this post that might help.
[http://ubuntuforums.org/showpost.php?p=2863967&postcount=2](http://ubuntuforums.org/showpost.php?p=2863967&postcount=2)

---

### Post by TerryChou on 2007-06-22
>  ping ubuntuforum.org
PING ubuntuforum.org (82.211.81.133) 56(84) bytes of data.

and then, it is like being dead...

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

