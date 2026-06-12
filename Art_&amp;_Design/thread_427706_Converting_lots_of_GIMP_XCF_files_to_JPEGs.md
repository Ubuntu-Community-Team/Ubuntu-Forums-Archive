---
title: "Converting lots of GIMP XCF files to JPEGs"
date: 2007-04-29
forum: Art &amp; Design
---

### Post by Ted_Smith on 2007-04-29
Can anyone tell me how to convert loads of GIMP XCF files to 100% quality JPEGs? I thought I could do it with imagemagicks convert tool : 

> convert -quality 100 *.xcf *.jpg

but I get "Segmentation fault" and it stops after the first one. 

Any ideas?

Thanks

Ted

---

### Post by Albi on 2007-04-29
Well if it works properly individually, you can create your own script

1)cd to the directory of files
2)ls
3)copy
4) open gedit
5) paste
6) use search and replace to add the commands to the list of files
7) add cd to the directory at the beginning of the script just to be sure
8) sudo chmod +x the script
9) run it

---

### Post by Ted_Smith on 2007-05-01
Yep, thanks for that. Good suggestion. But there must be an easier way.

I'm convinced this is probably a mistake on my part. I guess fundamentally I'm asking Imagemagick to "Convert all the xcfs to jpegs" but I expect it's choking on the naming scheme thinking that I want to call EVERY file *****.jpg? I would have thought it would know to assume the filename itself where * is used, but perhaps not? 

Surely, with a tool like Imagemagick, you can easily convert a folder of xcfs to jpegs in one go without resorting to the copying and pasting, finding and replacing in a script? 

Ted

---

### Post by Ted_Smith on 2007-05-13
> Surely, with a tool like Imagemagick, you can easily convert a folder of xcfs to jpegs in one go without resorting to the copying and pasting, finding and replacing in a script?

Anyone?

---

### Post by WamBamBoozle on 2011-04-17
5 years later ...

Here's a script for doing that. We prefer 'xcf2png' because png's is not "lossy" and 'xcf2png', unlike 'convert', knows how to deal with 'layers'.

```
#!/usr/bin/perl -w

# Ensure that every xcf file has a newer png

# We want to ensure that our master copies of images are in the GIMP
# native format, xcf. But we can't use most image browsers with xcf
# files, so we run this script to ensure that our directory has a newer
# copy of the GIMP image in PNG format for browsing.

# Takes one argument: the directory containing the gimp images to be
# converted

use strict;
use File::Find;
use File::Spec;

# call the shell and die noisily if appropriate

sub noisy {
    system(@_) == 0 or die "system(@_) failed: $?";
}

sub wanted {
    /\.xcf$/ || return;
    my $source = $_;
    s/\.xcf$/\.png/;
    my $source_modify_time = (-M $source);
    my $target_modify_time = (-M $_);
    return if $target_modify_time && $target_modify_time < $source_modify_time;
    print File::Spec->rel2abs($File::Find::name), "\n";
    noisy('xcf2png', $source, '-o', $_);
}

find(\&wanted, $ARGV[0]);

```

Of course, the best solution would be to extend (FStop, GThumb, what have you) to work directly with xcf files.

---

### Post by techunit on 2011-04-17
A little app called Phatch should do nicely. I use it for making appropriately sized icons.

Good Luck

---

### Post by WamBamBoozle on 2011-04-17
Icons of xcf (gimp) images for nautilus are done automatically with the package gnome-xcf-thumbnailer

As for Phatch -- does it know how to deal with layers? 'convert' was totally failing for that.

---

### Post by techunit on 2011-04-17
Should work fine. It should automatically flatten the layers. But I just realized this thread it about 4 years old.

---

