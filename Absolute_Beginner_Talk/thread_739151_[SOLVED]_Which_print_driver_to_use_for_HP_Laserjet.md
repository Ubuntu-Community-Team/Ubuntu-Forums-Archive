---
title: "[SOLVED] Which print driver to use for HP Laserjet 2100"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2008-03-29
Is there a way to know which of the several drivers that are listed in Ubuntu/Gutsy for the HP laserjet 2100 printer is the MOST / best suited for use with this printer, i.e. which one is the most up-to-date ?

Most all of the ones that are listed (except of the very first one - which strangely enough says "recommended" - but which is the only one that does not seem to work correct) will print the same test page.  But how do I know which one is the BEST to use for this printer ?

P. S. - I already went to the HP linux driver download page and what I see on there indicates that those drivers will not work if the printer is connected via parallel port.

Thanks.

---

### Post by linuxwizard on 2008-03-29
Look over this

[http://www.openprinting.org/show_printer.cgi?recnum=HP-LaserJet_2100](http://www.openprinting.org/show_printer.cgi?recnum=HP-LaserJet_2100)

---

### Post by wpshooter on 2008-04-06
How come when I go to this page and look up the supported devices for my HP Laserjet 2100 printer that it has a big NO in the parallel port column of the grid ?

[http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)

My HP 2100 only has a parallel port and some type of port of use on an Apple computer.  I am not using an Apple.  I have a IBM compatible built by me.

How can this printer driver NOT be compatible with / work on a parallel port ?  

Are there HP 2100 printers that have different port configurations from the one that I have ?

Thanks.

---

### Post by wpshooter on 2008-04-08
Your question #29237 on HPLIP changed:
[https://answers.launchpad.net/hplip/+question/29237](https://answers.launchpad.net/hplip/+question/29237)

    Status: Open => Answered

dwelch91 proposed the following answer:
This is an error in the data (models.dat). We will correct this in future versions.

The entry in the table under "Parallel" that says "No" will not prevent you from using parallel, it merely means that we _thought_ that the printer did not support parallel.

On Tue, Apr 8, 2008 at 8:02 AM, wpshooter < [email]question29237@answers.launchpad.net[/email]> wrote:

> New question #29237 on HPLIP:
> [https://answers.launchpad.net/hplip/+question/29237](https://answers.launchpad.net/hplip/+question/29237)
>
> Why is it that on this grid that I see on this HPLIP site that for the 
> HP laserjet 2100 (and many other models on the grid) the 
> listing/parameter under the "Parallel" column of the grid is NO ?
>
> My HP laserjet only has a parallel port interface and an AppleTalk 
> interface.  The Apple interface would not be applicable in my case 
> since I am not using an Apple computer.
>
> Does this "NO" in the parallel port column of this grid means that the 
> drivers listed here can not be used via a printer like the HP 2100 
> which is connected via a parallel/lpt1 port ?
>
> Thanks.

---

