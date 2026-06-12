---
title: "HP 4160 Printer problems"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by squig on 2007-02-24
Problems printing with HP printer. I have installed/reinstalled cups and hplip via symantec, then went  to [http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html) and did the manual install once and the Installer the second time. Problems persist. Does anyone know anything about this problem? Any help appreciated. 

When I send a print job to the printer, both lights on the printer flash *really* fast, and nothing prints. System reports printer as busy. I have to delete print job, restart printer, open terminal mode, and enter:
sudo /etc/init.d/cupsys restart
sudo /etc/init.d/hplip restart

Then the printer will usually work again, for one print job. Then I have to do the whole process over again.

Sometimes when I enter 

sudo /etc/init.d/hplip restart

I get 

Stopping hpiod: /etc/init.d/hplip: line 57: kill: (991) - No such process
                                           [FAILED]


Usually, for both processes, I get this: 

amy@amy-laptop:~$ sudo /etc/init.d/cupsys restart
Password:
 * Restarting Common Unix Printing System: cupsd                         [ ok ]
amy@amy-laptop:~$ sudo /etc/init.d/hplip restart
Stopping hpiod:                                            [  OK  ]
Stopping hpssd:                                            [  OK  ]
Starting hpiod:                                            [  OK  ]
Starting hpssd:                                            [  OK  ]
amy@amy-laptop:~$ sudo /etc/init.d/cupsys restart
 * Restarting Common Unix Printing System: cupsd                         [ ok ]
amy@amy-laptop:~$ sudo /etc/init.d/hplip restart
Stopping hpiod:                                            [  OK  ]
Stopping hpssd:                                            [  OK  ]
Starting hpiod:                                            [  OK  ]
Starting hpssd:                                            [  OK  ]
amy@amy-laptop:~$

The only other thing that seemed red-flaggish when I ran the installer this morning was this message at the very end of the process:

HP Linux Imaging and Printing System (ver. 1.7.1)
Printer/Fax Setup Utility ver. 4.3

Copyright (c) 2003-6 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Done.

I have no idea what it means.

Any help greatly appreciated. Many thanks.
~A






sudo /etc/init.d/hplip restart
sudo /etc/init.d/hplip restart

---

### Post by NewOldTimer on 2007-02-25
look here....

[http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=fT9&q=X+Error+BadDevice+input+device&btnG=Search](http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=fT9&q=X+Error+BadDevice+input+device&btnG=Search)

and if needed...

[http://ubuntuforums.org/showthread.php?t=368319&highlight=commenting+out](http://ubuntuforums.org/showthread.php?t=368319&highlight=commenting+out)

hope that works for you:)

---

