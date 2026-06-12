---
title: "Possible to share out folder without SAMBA?"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-08-07
If I share out my /home/test folder, what do I need to configure on my box (without installing SAMBA, if possible) and how do my client pc access the shared folder?

Thanks!

---

### Post by cantormath on 2006-08-07
> **Akhran said:**
> If I share out my /home/test folder, what do I need to configure on my box (without installing SAMBA, if possible) and how do my client pc access the shared folder?

Thanks!

you could set up an ftp or use an ssh client from a windows box to connect to the linux box and share.
you dont have to set up a samba server to grab stuff of a windows box.  windows machines should show up in Places>Network Server.

---

### Post by Akhran on 2006-08-07
Thanks for the ftp tip. 

I have tried using putty to ssh into the linux box, but how do I transfer files from the linux folder into the windows box? Mind elaboring on how to use an ssh client from a windows box to connect to the linux box and share?

Thanks, much appreciated.



> **cantormath said:**
> you could set up an ftp or use an ssh client from a windows box to connect to the linux box and share.
you dont have to set up a samba server to grab stuff of a windows box.  windows machines should show up in Places>Network Server.

---

### Post by arjun.shankar on 2006-08-07
You can use pscp (part of  PuTTY)

Here is an extract from the online doc:
**[http://the.earth.li/~sgtatham/putty/0.58/htmldoc/Chapter5.html](http://the.earth.li/~sgtatham/putty/0.58/htmldoc/Chapter5.html)**


[B]Chapter 5: Using PSCP to transfer files securely

PSCP, the PuTTY Secure Copy client, is a tool for transferring files securely between computers using an SSH connection. 

If you have an SSH-2 server, you might prefer PSFTP (see chapter 6) for interactive use. PSFTP does not in general work with SSH-1 servers, however. 
5.1 Starting PSCP

PSCP is a command line application. This means that you cannot just double-click on its icon to run it and instead you have to bring up a console window. With Windows 95, 98, and ME, this is called an &#8216;MS-DOS Prompt&#8217; and with Windows NT, 2000, and XP, it is called a &#8216;Command Prompt&#8217;. It should be available from the Programs section of your Start Menu. 

To start PSCP it will need either to be on your PATH or in your current directory. To add the directory containing PSCP to your PATH environment variable, type into the console window: 
set PATH=C:\path\to\putty\directory;%PATH%

This will only work for the lifetime of that particular console window. To set your PATH more permanently on Windows NT, 2000, and XP, use the Environment tab of the System Control Panel. On Windows 95, 98, and ME, you will need to edit your AUTOEXEC.BAT to include a set command like the one above. 
5.2 PSCP Usage

Once you've got a console window to type into, you can just type pscp on its own to bring up a usage message. This tells you the version of PSCP you're using, and gives you a brief summary of how to use PSCP: 
Z:\owendadmin>pscp
PuTTY Secure Copy client
Release 0.58
Usage: pscp [options] [user@]host:source target
       pscp [options] source [source...] [user@]host:target
       pscp [options] -ls [user@]host:filespec
Options:
  -V        print version information and exit
  -pgpfp    print PGP key fingerprints and exit
  -p        preserve file attributes
  -q        quiet, don't show statistics
  -r        copy directories recursively
  -v        show verbose messages
  -load sessname  Load settings from saved session
  -P port   connect to specified port
  -l user   connect with specified username
  -pw passw login with specified password
  -1 -2     force use of particular SSH protocol version
  -4 -6     force use of IPv4 or IPv6
  -C        enable compression
  -i key    private key file for authentication
  -batch    disable all interactive prompts
  -unsafe   allow server-side wildcards (DANGEROUS)
  -sftp     force use of SFTP protocol
  -scp      force use of SCP protocol

(PSCP's interface is much like the Unix scp command, if you're familiar with that.) 
5.2.1 The basics

To receive (a) file(s) from a remote server: 
pscp [options] [user@]host:source target

So to copy the file /etc/hosts from the server example.com as user fred to the file c:\temp\example-hosts.txt, you would type: 
pscp [email]fred@example.com[/email]:/etc/hosts c:\temp\example-hosts.txt

To send (a) file(s) to a remote server: 
pscp [options] source [source...] [user@]host:target

So to copy the local file c:\documents\foo.txt to the server example.com as user fred to the file /tmp/foo you would type: 
pscp c:\documents\foo.txt [email]fred@example.com[/email]:/tmp/foo

You can use wildcards to transfer multiple files in either direction, like this: 
pscp c:\documents\*.doc [email]fred@example.com[/email]:docfiles
pscp [email]fred@example.com[/email]:source/*.c c:\source
[/B]

---

