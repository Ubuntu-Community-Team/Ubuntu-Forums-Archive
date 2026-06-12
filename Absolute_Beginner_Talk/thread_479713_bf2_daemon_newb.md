---
title: "bf2 daemon newb"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by doughardy on 2007-06-20
running >Linux ubuntu 2.6.20-15-server 


installed >bf2-linuxded-1.1.2963-795-installer.sh  everything works fine server starts

installed  > mono-1.1.12.1_0-installer.bin

tested to see if installed  ok there as below
xxxxxxx@ubuntu:~$ mono -V
Mono JIT compiler version 1.2.3.1, (C) 2002-2006 Novell, Inc and Contributors. [www.mono-project.com](www.mono-project.com)
        TLS:           __thread
        GC:            Included Boehm (with typed GC)
        SIGSEGV:       normal
        Architecture:  x86
        Disabled:      none
xxxxxxx@ubuntu:~$ 

installed  BF2CCD_1.4.2446


 installed on xp machine BF2CC_Client_1.4.2452


and modmanager-v1.6

i am using a SSH Secure Shell Client with screen command  from the xp machine
inputting this command >mono bf2ccd.exe and get this below

Optional command line switches:
  -configdaemon        Goes through the reconfiguration section
  -ranked              Runs the server in ranked mode
  -showlog             Shows log to screen
  -lockdemorec         Locks down demo recording (nobody can change)
  -locknetsettings     Locks down BF2 network settings (nobody can change)
  -nocoop              Prevents any user from being able to run a Coop (gpm_coop) server
  -noquitprompts       No 'confirm' prompts when closing.
  -autostart [profile] Immediatly starts the server.
  -playerlimit         Nobody can exceed maximum player limit.
  -skipportchecks      Skips open port checking for RCON and Daemon.
  -dontpassthru       Dont pass + commands through to the executable.
  -debugmode              Shows debug output for diagnostics.
  -kill                Kills the daemon process started from this dir.
  -skipdotnetcheck     Bypasses the .NET Framework check and associated Error dialogue boxes.
  +config              BF2 serversettings.con (full path and file)
  +mapList             BF2 maplist.con (full path and file)
  +pbpath              BF2 redirect of the punkbuster path

im not sure on what commands to enter to configure the daemon  being  a newb to linux any help would be appreciated thx all

---

### Post by Choc_Salties on 2007-11-10
if you've never used bf2ccd on that machine before (which i assume you havent) then you need to run bf2ccd with the -configdaemon switch - that will ask you all the important questions such as an admin username and password you can be used in conjunction with the BF2cc client later from winblows or other OS...

---

