---
title: "GNUmp3D help I know it's ancient but"
date: 2014-07-12
forum: Any Other OS
---

### Post by Evil Wayz on 2014-07-12
It's a really nice program.  I get the following error when I enter the command: gnump3d &

Can't use an undefined value as a HASH reference at /usr/share/perl5/gnump3d/config.pm line 99.

When I got to that line in the file it reads as follows: my %HASH= %$hash;

The entire piece of code looks like this:

sub getConfig
{
my ( $key, $default ) = ( @_ );
my $value = undef;

my %HASH= %$hash;


if ( !defined( $value ) )
{
if( defined( $HASH{ $key } ) )
{
$value = $HASH{ $key };
}
else
{
return( $default );
}
}
return( $value );
}


If someone with some perl knowledge could help it would be really appreciated as I love this program and would like to keep using it. Thanks in advance Ubuntu peeps.

EDIT:  If anyone knows of a simple gnump3d alternative please let me know.  I plan to share my files with friends and family not on my LAN.

---

### Post by tgalati4 on 2014-07-12
I ran gnump3d for several years as a church music server and it performed that function well.  I would do the following:

Run *gnump3d* without the & and see if there are any messages.

Sometimes errors are really triggered at the line before.  So the previous line sets $value to undefined which may be problematic in newer versions of PERL.

How did you install gnump3d?  Did you update or change or have different versions of PERL installed?

Because the last release was 2007 timeframe, you might be stuck running it in a vm with an older (and unsupported) os such as 10.04.  What version of Ubuntu are you trying to install it in?

---

### Post by Evil Wayz on 2014-07-12
Running just gnump3d gets the same error about line 99.  would posting the entire config.pm help?

I installed gnump3d by unzipping hte tar and then doing make install.
I'm using linux mint 17 right now the last time i had ubuntu was 10 and it worked fine so maybe its the perl Im running.  I have no idea what version of perl it last worked with.  COuld I run a virtual machine and have it accessible over the web?

---

### Post by tgalati4 on 2014-07-12
You have a few options:

Find an old machine and perform a clean install of 10.04 and gnump3d and run that for a while.  Then do some research on what version of PERL was running on 10.04 and what you are running in Mint17:

```
apt-cache policy perl
```

Then check the [perl]("http://www.perl.org/") website and go through the release changes and see what changes have been made (a lot).

I doubt that the configurator script will be the only problem that you run into.  Because the program does not have an active maintainer, it will only work (or has only worked) with the frameworks that were available in 2007.  Anything newer will cause breakage.  That is also why you need to have the older OS working so you can compare expected behavior under 10.04 with behavior under 14.04.

If there are only a few tweaks needed to the PERL code then you can document them in this thread.  If you have the time and inclination, you can become the maintainer of version 4!

Yes, you should be able to use a virtual machine to run a 10.04 instance and run gnump3d and serve files to the web.  It will be slower than a native installation, but that might be acceptable.  I would be more concerned with security, since 10.04 is old, not supported, and if there is a security breech, do you really want an infected vm on your system?

---

### Post by Evil Wayz on 2014-07-12
Alright i see i have a lot of work to do, I'll post back if I find anything during my travels.  Thanks for replying.

---

### Post by oldos2er on 2014-07-13
Moved to Other OS/Distro Support.

---

