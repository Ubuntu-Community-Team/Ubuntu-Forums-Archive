---
title: "running graphing perl script?"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by meniscus on 2006-11-27
Im running a perl script to graph the harddrive temperature of which tutorial i got from here

[http://martybugs.net/linux/hddtemp.cgi](http://martybugs.net/linux/hddtemp.cgi)

I run it using the command

```
meniscus@meniscot:/usr/local/bin$ rrd_hddtemp.pl
```

and i got this error

```
Can't locate RRDs.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/local/bin/rrd_hddtemp.pl line 8.
BEGIN failed--compilation aborted at /usr/local/bin/rrd_hddtemp.pl line 8.

```

Whats going on? I followed the tutorial religiously!

---

### Post by cilynx on 2006-11-27
You're missing a perl module that your script needs...

```
sudo apt-get install librrds-perl
```

See how that does for you...

---

### Post by meniscus on 2006-11-27
Thank you. I made some progress. Now ive just got these error messages

The folder /var/lib/rrd exists


meniscus@meniscot:/usr/local/bin$ rrd_hddtemp.pl
SAMSUNG SP1213N (/dev/hda) temp:  degrees C
creating rrd database for /dev/hda...
/usr/local/bin/rrd_hddtemp.pl: unable to generate hda graph: opening '/var/lib/rrd/hda.rrd': No such file or directory
/usr/local/bin/rrd_hddtemp.pl: unable to generate hda graph: opening '/var/lib/rrd/hda.rrd': No such file or directory
/usr/local/bin/rrd_hddtemp.pl: unable to generate hda graph: opening '/var/lib/rrd/hda.rrd': No such file or directory
/usr/local/bin/rrd_hddtemp.pl: unable to generate hda graph: opening '/var/lib/rrd/hda.rrd': No such file or directory


The folder /var/lib/rrd exists
Shold the script not generate the graphs?

---

### Post by jsilve1 on 2006-11-27
> **meniscus said:**
> 
Whats going on? I followed the tutorial religiously!

I think you can solve the problem by installing the  "librrds-perl" package

```
sudo apt-get install librrds-perl
```

---

### Post by cilynx on 2006-11-27
/var/lib/rrd/ is a system folder, ie only writable by root.  You're running the script as a user.  You're going to have to either open up permissions on the folder or run the script under sudo.

---

### Post by meniscus on 2006-11-27
Sorry for my incompetence!

It says once the operation of the script is verified, it can be automatically scheduled to run periodically. 

T> o get it to run every 5 minutes, add the following to /etc/crontab:

# get hdd temperatures
*/5 * * * * root /usr/local/bin/rrd_hddtemp.pl > /dev/null



Is it just a matter a pasting in these lines to /etc/crontab?

/etc/crontab doesnt actually exist on my machine. It has cron.d cron.daily, cron.daily, cron.monthly, cron.weekly......

but no crontab!

Should i just paste it in to 1 of these? (daily weekly monthly etc)?

---

### Post by meniscus on 2006-11-27
sorry! I was looking at the folders!

I pasted it into the crontab text file. Do i need to restart my machine for the settings to take effect?

---

### Post by cilynx on 2006-11-27
The proper way to add content to crontab is
```
crontab -e
```
To add to root's crontab (what you need in this example)
```
sudo crontab -e
```
This command opens up an editor to edit the crontab then reloads cron to make sure the updates make sense

---

### Post by meniscus on 2006-11-28
Thank you for that. I was using the command

```
sudo gedit "filename" 
```

for editing stuff in the file system.


Its still not working though.

The graphs are being displayed in /var/www/html/rrdtool/ but there is no information in them


Here is that fellas sript. I changed it to monitor hda instead of hdc(which he graphed)


[PHP]#!/usr/bin/perl
#
# copyright Martin Pot 2003
# http://martybugs.net/linux/hddtemp.cgi
#
# rrd_hddtemp.pl

use RRDs;

# define location of rrdtool databases
my $rrd = '/var/lib/rrd';
# define location of images
my $img = '/var/www/html/rrdtool';

# process data for each specified HDD (add/delete as required)
&ProcessHDD("hda", "SAMSUNG SP1213N");
#&ProcessHDD("hdb", "primary slave");
#&ProcessHDD("hdc", "40GB Seagate");
#&ProcessHDD("hdd", "secondary slave");

sub ProcessHDD
{
# process HDD
# inputs: $_[0]: hdd (ie, hda, etc)
#         $_[1]: hdd description

	# get hdd temp for master drive on secondary IDE channel
	my $temp=`/usr/local/sbin/hddtemp -n /dev/$_[0]`;
	# remove eol chars and white space
	$temp =~ s/[\n ]//g;
	
	print "$_[1] (/dev/$_[0]) temp: $temp degrees C\n";

	# if rrdtool database doesn't exist, create it
	if (! -e "$rrd/$_[0].rrd")
	{
		print "creating rrd database for /dev/$_[0]...\n";
		RRDs::create "$rrd/$_[0].rrd",
			"-s 300",
			"DS:temp:GAUGE:600:0:100",
			"RRA:AVERAGE:0.5:1:576",
			"RRA:AVERAGE:0.5:6:672",
			"RRA:AVERAGE:0.5:24:732",
			"RRA:AVERAGE:0.5:144:1460";
	}

	# insert value into rrd
	RRDs::update "$rrd/$_[0].rrd",
		"-t", "temp",
		"N:$temp";

	# create graphs
	&CreateGraph($_[0], "day", $_[1]);
	&CreateGraph($_[0], "week", $_[1]);
	&CreateGraph($_[0], "month", $_[1]);
	&CreateGraph($_[0], "year", $_[1]);
}

sub CreateGraph
{
# creates graph
# inputs: $_[0]: hdd name (ie, hda, etc)
#         $_[1]: interval (ie, day, week, month, year)
#         $_[2]: hdd description

	RRDs::graph "$img/$_[0]-$_[1].png",
		"--lazy",
		"--alt-y-grid",
		"-s -1$_[1]",
		"-t hdd temperature :: $_[2] (/dev/$_[0])",
		"-h", "80", "-w", "600",
		"-a", "PNG",
		"-v degrees C",
		"DEF:temp=$rrd/$_[0].rrd:temp:AVERAGE",
		"LINE2:temp#0000FF:$_[2] (/dev/$_[0])",
		"GPRINT:temp:MIN:  Min\\: %2.lf",
		"GPRINT:temp:MAX: Max\\: %2.lf",
		"GPRINT:temp:AVERAGE: Avg\\: %4.1lf",
		"GPRINT:temp:LAST: Current\\: %2.lf degrees C\\n";
	if ($ERROR = RRDs::error) { print "$0: unable to generate $_[0] graph: $ERROR\n"; }
}

[/PHP]



Ive changed everything i can think of but cant get the temperature values to display! Am i missing something?

---

