---
title: "Removing nfs and rcpbind"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by mouko on 2007-12-13
So I installed and subsequently removed Limewire. (I installed from their site, if it makes any difference.  Removed with, "sudo apt-get remove limewire-basic")

Now if I do socklist or nmap, I see that I have ports 111 and 2049 open and something is running on them.  It isn't terribly worrying, as I have firestarter installed and blocking most ports, but I'd still like to know if anybody knows how to remove the programs that are using these ports.

---

### Post by mkoyle on 2008-01-16
So 

```
nmap --open localhost
```

says that nfs is on 2049 and rcpbind is on 111?

```
sudo apt-get install unfs3 nfs-client nfs-common nfs-kernel-server nfs-user-server nfs-server
```

That might get rid of it for you; I am not sure what package was used to install nfs, but it seems that rcpbind and nfs are both 'nfs'-related.

If that doesn't get rid of it, the following will help you find which package is the trouble... but might take some looking on your par.  The following command and output shows everything that has 'nfs' in its description.  The following list shows all of the default packages (installed on my system).  When you run the command and compare your output with this, any additional packages that you do not recognize are probably the culprits:

```
matthew@Judith:~$ sudo apt-cache search --installed nfs
backuppc - high-performance, enterprise-grade system for backing up PCs
initramfs-tools - tools for generating an initramfs
kdenetwork-filesharing - network filesharing configuration module for KDE
libgssapi-dev - header files and docs for libgssapi
libgssapi2 - A mechanism-switch gssapi library
liblockfile1 - NFS-safe locking library, includes dotlockfile program
libnfsidmap-dev - header files and docs for libnfsidmap
libnfsidmap2 - An nfs idmapping library
librpcsecgss-dev - header files and docs for librpcsecgss
librpcsecgss3 - allows secure rpc communication using the rpcsec_gss protocol
manpages - Manual pages about using a GNU/Linux system
nbd-client - the Network Block Device client
nbd-server - the Network Block Device server
nfs-common - NFS support files common to client and server
nfs-kernel-server - support for NFS kernel server
portmap - The RPC portmapper
tcpdump - A powerful tool for network monitoring and data acquisition
texlive-fonts-extra - TeX Live: Extra fonts
texlive-fonts-recommended - TeX Live: Recommended fonts
texlive-lang-vietnamese - TeX Live: Vietnamese
texlive-latex-base - TeX Live: Basic LaTeX packages
bootcd - run your system from cd without need for disks
cfs - Cryptographic Filesystem
collectd - statistics collection daemon
dsniff - Various tools to sniff network traffic for cleartext insecurities
fai-nfsroot - Fully Automatic Installation nfsroot package
fam - File Alteration Monitor
funionfs - user-space directory concatenation
gnats-user - The GNU problem report management system (client tools)
gnomp3 - MP3 player for large MP3 collections
gxemul - machine emulator for multiple architectures
libfile-nfslock-perl - perl module to do NFS (or not) locking
libposixlock-ruby - posix locking for ruby
libposixlock-ruby1.8 - posix locking for ruby
libroxen-tokenfs - Token File System module for the Roxen Challenger web server
libsfs0c2 - Self-Certifying File System shared libraries
libsfs0c2-dev - Self-Certifying File System development files
live-initramfs - Debian Live initramfs hook
manpages-de - German manpages
manpages-fr - French version of the manual pages about using GNU/Linux
manpages-pl - Polish man pages
manpages-pt - Portuguese Versions of the Manual Pages
manpages-tr - Turkish version of the manual pages
mb2md - Converting Mbox mailboxes to Maildir format
mondo - powerful disaster recovery suite
mondo-doc - manual for Mondo, a powerful disaster recovery suite
mythbuntu-live-autostart - Mythbuntu Live CD Configuration
nfs-user-server - User space NFS server
nfsboot - Allow clients to boot over the network
nfsbooted - Prepares your image for nfs boot
p3nfs - to mount the file systems on the Psion/Symbian PDA/Phone
plptools - Access a Psion PDA over a serial link
portsentry - Portscan detection daemon
prokyon3 - A mp3 and ogg/vorbis manager and tag editor
replicator - automate new computer installations in a networked site.
sdd - File duplication and conversion tool, similar to 'dd'
sfs-client - Self-Certifying File System client
sfs-common - Self-Certifying File System common files
sfs-server - Self-Certifying File System server
sigit - A small utility to change signatures randomly
tiger-otheros - Scripts to run Tiger in other operating systems
udpcast - multicast file transfer tool
ugidd - NFS UID mapping daemon
unfs3 - User-space NFSv3 Server
unionfs-source - Source for the union filesystem
unionfs-tools - Tools to manage unionfs filesystems
kdelibs4c2a - core libraries and binaries for all KDE applications

```

Good luck!

--Matthew

---

