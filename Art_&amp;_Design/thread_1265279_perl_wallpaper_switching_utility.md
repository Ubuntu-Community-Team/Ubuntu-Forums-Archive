---
title: "perl wallpaper switching utility"
date: 2009-09-13
forum: Art &amp; Design
---

### Post by dv3500ea on 2009-09-13
I have created a small self-contained program in perl which can change wallpaper to a certain image file, randomly change wallpaper or randomly change wallpaper periodically. To install it, copy the source code into a text editor and save as /usr/bin/change-wallpaper then run ```
change-wallpaper install
```. You can find out how to use it by running ```
change-wallpaper help
```. It works with gnome but could be ported to KDE or XFCE if there is an equivalent to gconftool-2 in either. This could be done by changing the system call in sub changewallpaperto. It should also be relatively simple to create a GUI frontend for it. I use this application because I like my wallpaper to change. I have posted it here in case it is of any use to anyone else.
```

#!/usr/bin/perl
#This program is  free software licenced under the GNU General Public.
#You can get a copy from www.gnu.org
#You may edit, copy or create derivatives from this work as long as you licence it under the same licence.
use warnings;
use strict;

my @globvar = ();
my $globdir = '';

my %options = (
    stop => ($ARGV[0] =~ /stop/i ? 1 : ''),
    once => (!@ARGV || $ARGV[0] =~ /once/i ? 1 : ''),
    loop => ($ARGV[0] =~ /loop/i ? 1 : ''),
    help => ($ARGV[0] =~ /help/i ? 1 : ''),
    change_image_dir => ($ARGV[0] =~ /dir/i ? 1 : ''),
    change_frequency => ($ARGV[0] =~ /freq/i ? 1 : ''),
    install => ($ARGV[0] =~ /install/i ? 1 : ''),
    wizard => ($ARGV[0] =~ /wizard/i ? 1 : ''),
    to => ($ARGV[0] =~ /to/i ? 1 : ''),
    licence => ($ARGV[0] =~ /licence/i ? 1 : ''),
    source => ($ARGV[0] =~ /source/i ? 1 : ''),
    uninstall => ($ARGV[0] =~ /uninstall/i ? 1 : '')
);

sub getconfig {#1 = changefreq, 2 = on/off, 3 = bgdir
    my $i = 1; my $arg = shift;
    open (my $in, 'change-wallpaper.config') || die ('can\'t open config file for reading');
    while (<$in>) {
        if ($i == $arg) {
            return $_;        
        }        
        $i += 1;
    }
}

sub setconfig {
    open (my $out, '>', 'change-wallpaper.config') || die ('can\'t open config file for writing');
    print $out $_[0];
    close $out;
}

sub getglob {
    $globdir = getconfig(3);
    $globdir =~ s/\n//;
    my @formats = ('jp*', 'gif', 'bmp', 'png');
    my @tempglob = ();
    foreach (@formats) {
        #print "$globdir/*.$_\n";
        @tempglob = glob("$globdir/*.$_");
        foreach (@tempglob) {
            #print "
            #$_";
            push(@globvar, $_);
        }    
    }
}

sub changewallpaperto {#
    my $filepath = ($globdir ? '' : getconfig(3)) . '/' . shift(@_); 
    $filepath =~ s/\n//;
    my @globbed = glob($filepath);
    $filepath = $globbed[0];
    print "\n$filepath\n";
    system('gconftool-2 --type string --set /desktop/gnome/background/picture_filename ' . $filepath);
}

sub randchange {
    getglob();
    #print "debug: ".$globvar[int(rand() * @globvar)];
    changewallpaperto($globvar[int(rand() * @globvar)]);
}

if ($options{wizard}) {
    print "
    Welcome to the change-wallpaper wizard, how may I help you.

    Enter 0 to install, 1 to get help on this program, 2 to see the licence, 3 to see the      source code, 
    4 to change the desktop background, 5 to randomly switch the wallpaper, 6 to change
    the directory in which to search randomly for wallpaper, 7 to change the wallpaper
    every given amount of seconds (15 is default), 8 to change this value, 9 to stop all running
    switcher loops or anything elsecd to exit.
    
";

    my $option = <stdin>;
    if ($option == 0) {
        $options{install} = 1;
    }
    if ($option == 1) {
        $options{help} = 1;
    }
    if ($option == 2) {
        $options{licence} = 1;
    }
    if ($option == 3) {
        $options{source} = 1;
    }
    if ($option == 4) {
        $options{to} = 1;
        print "ENTER IMAGE PATH\n";
        $ARGV[1] = <stdin>;
    }
    if ($option == 5) {
        $options{once} = 1;
    }
    if ($option == 6) {
        $options{change_image_dir} = 1;
        print "ENTER DIRECTORY PATH\n";
        $ARGV[1] = <stdin>;
    }
    if ($option == 7) {
        $options{loop} = 1;
    }
    if ($option == 8) {
        $options{change_frequency} = 1;
        print "ENTER NUMBER OF SECONS TO WAIT\n";
        $ARGV[1] = <stdin>;
    }
    if ($option == 9) {
        $options{stop} = 1;
    }
}

if ($options{help}) {
    print "
    synopsis:    change-wallpaper [to|once|loop|stop|freq|dir|install|wizard|help|licence|source|uninstall] [argument]

    change-wallpaper is a command-line utility, written in perl, to change the wallpaper on the Gnome Desktop.
    
    Commands can be typed into a terminal or run by pressing alt-f2, typing them into the box and pressing enter, although for those which output text,         the text will not be visible.

    To get help run: change-wallpaper help
    This command takes no arguments. This command outputs text. This command can be run without installing.

    To see the licence run: change-wallpaper licence
    This command takes no arguments. This command outputs text. This command can be run without installing.

    To see the source code run: change-wallpaper source
    This command takes no arguments. This command outputs text. This command can be run without installing.

    To run a helper wizard run: change-wallpaper wizard
    This command takes no arguments. This command outputs text. This command can be run without installing but some subsequent actions will not work.

    To install or reset defaults run: change-wallpaper install
    This command takes no arguments. This command can be run without installing.

    To uninstall and remove the uninstalled file run: change-wallpaper uninstall
    This command takes no arguments. This command can be run without installing.

    To change wallpaper to a file run: change-wallpaper to <file_path>
    This command requires installation. This command takes one argument, the path of the image file to change to.

    To change wallpaper to a random file in the given directory run: change-wallpaper once
    This command requires installation. This command can also be run by running: change-wallpaper

    To change the directory in which this program randomly searches for images run: change-wallpaper dir <directory-path>
    This command requires installation. This command takes one argument, the path of the directory to change to; DEFAULT : ~/Pictures.

    To randomly change wallpaper every given number of seconds run: change-wallpaper loop
    This command requires installation. 

    To change the number of seconds to wait run: change-wallpaper freq <seconds>
    This command requires installation. This command takes one argument, the number of seconds to wait; DEFAULT : 15.

    To stop all running change-wallpaper loops run: change-wallpaper stop
    This command requires installation. 

    To change wallpaper on login go to system->preferences->startup applications, click 'add', type 'change-wallpaper once' and press enter.

    To allways change wallpaper every given number of seconds go to system->preferences->startup applications, click 'add', type 
    'change-wallpaper loop' and press enter.

    Troubleshooting: remember to install
";
}

if ($options{licence}) {
    print "
    This program is  free software licenced under the GNU General Public.
    You can get a copy from www.gnu.org
    You may edit, copy or create derivatives from this work as long as you licence it under the same licence.
    ";
}

if ($options{source}) {
    open (my $source, 'change-wallpaper') || die ('can\'t view source, check to see this file is called change-wallpaper');
    my $i = 1;
    while (<$source>) {
        print (($i < 10 ? '0' : '').($i < 100 ? '0' : '').$i .' ' . $_ . "\n");
        $i += 1;
    }
}

if ($options{install}) {
    setconfig("15\n1\n~/Pictures");
}

if ($options{uninstall}) {
    system("rm change-wallpaper.config");
    system("rm change-wallpaper");    
}

if ($options{change_image_dir}) {
    setconfig(getconfig(1).getconfig(2).$ARGV[1]);
}

if ($options{change_frequency}) {
    setconfig($ARGV[1]."\n".getconfig(2).getconfig(3));
}
if ($options{stop}) {
    setconfig(getconfig(1)."0\n".getconfig(3));
}

if ($options{to}) {
    unless ($options{stop}) {
        changewallpaperto($ARGV[1]);
    }
}

if ($options{once}) {
    randchange();
}

if ($options{loop}) {
    setconfig(getconfig(1)."1\n".getconfig(3));
    my $loop = getconfig(2);
    while ($loop > 0) {
        #print "
        #checking config : " . getconfig(1).getconfig(2).getconfig(3)."        
        #";
        $loop = getconfig(2);
        #print "
        #$loop
        #";
        randchange();
        sleep(getconfig(1));
    }
}

```

EDIT: you may have to run ```
chmod +x /usr/bin/change-wallpaper
```

---

