---
title: "Linux Counter /machine-update Problems."
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by ICUR2Ys on 2007-06-30
When I try to run machine-update -i for linux counter I get the following:

dace@dace-desktop:~$ LinuxCounter/machine-update -i
LinuxCounter/machine-update: line 25: use: command not found
LinuxCounter/machine-update: line 26: use: command not found
LinuxCounter/machine-update: line 28: our: command not found
LinuxCounter/machine-update: line 29: our: command not found
LinuxCounter/machine-update: line 30: our: command not found
LinuxCounter/machine-update: line 31: syntax error near unexpected token `('
LinuxCounter/machine-update: line 31: `use vars qw(%values %oldvalues $errordata $debugdata %files); # data that is sent'
dace@dace-desktop:~$ 

Beginning part of actual script:

# This script registers or updates a machine's info in the # counter. The info registered will show up in the list of # machines on your homepage.
#
# Instructions for use:
#
#     * Save machine-update to a file named "machine-# # # # update" in any convenient place
#     * From a terminal window, change directory to that # # place.
#     * Change it to be executable (chmod +x machine-update)
#     * Run "./machine-update -i" to enter information
#     * Run "./machine-update -m" to send mail
#     * Run "./machine-update -c" to add it to your crontab # file 
#
#!/usr/bin/perl -w
# For Emacs: -*- mode:cperl; mode:folding; -*-
#
# Get a machine's critical features, And mail/http them to the Linux Counter
#
# (c) 1999 - Harald Tveit Alvestrand, the Linux Counter Project
#     2003 - PetaMem Group ([www.petamem.com](www.petamem.com))
# License:   GNU Copyleft - see bottom of file.
# Changelog: see even more bottom of the file
#
# As a matter of courtesy, if you change this file on your own,
# make sure it does NOT mail to the counter!
#
use strict;
use POSIX;

our $VERSION     = '0.30';
our $CVS_VERSION = '$Revision: 1.8 $ $Date: 2007/01/21 17:22:50 $ $Author: patrick $';
our $IsInTestHarness;
use vars qw(%values %oldvalues $errordata $debugdata %files); # data that is sent
use vars qw($progname %option $mailprogram);
use vars qw(%is_sys_account %is_user %is_account);

# stuff that controls defaults for passwdscan & accounts subroutines
my ($UID_MIN, $UID_MAX, $got_defs) = (100, 65533, '');

# Make sure nothing happens, so that the script's routines
# can be debugged from another file
return 1 if($IsInTestHarness);


I think that I need to load something to make this work, but I don't know what.

---

