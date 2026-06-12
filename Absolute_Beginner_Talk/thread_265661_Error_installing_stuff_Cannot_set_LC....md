---
title: "Error installing stuff Cannot set LC..."
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by BrianAT on 2006-09-26
Anytime I install anything I get the following (copied from another post somewhere since the t:
```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US:en_GB:en",
        LC_ALL = (unset)
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory 
```

I also get something along the lines of the following after the above:
```
gtk-WARNING ** locale not supported by C library.
        Using the fallback 'C' locale. at usr/share/pearl5/Debconf/FrontEnd/Gnom
e.pm line 54, <> 1.
gtk-WARNING ** locale not supported by C library at usr/shar/pearl5/Debconf/Fr
ontEnd/Gnome.pm line 54, <> 1.
gtk-WARNING ** locale not supported by C library.
        Using the fallback 'C' locale. at usr/share/pearl5/Debconf/FrontEnd/Gnom
e.pm line 60, <> 1.
gtk-WARNING ** locale not supported by C library at usr/shar/pearl5/Debconf/Fr
ontEnd/Gnome.pm line 60, <> 1.
```

Here are lines 52 to 61 of the gnome.pm mentioned above:
```
	else {
		@ARGV=@ARGV_for_gnome; # temporary change at first
		Gnome2::Program->init('GNOME Debconf', '2.0');
		exit(0); # success
	}
	
	my @gnome_sucks=@ARGV;
	@ARGV=@ARGV_for_gnome;
	Gnome2::Program->init('GNOME Debconf', '2.0');
	@ARGV=@gnome_sucks;
```

I can't install the English pack as it freezes the system up anytime the computer hits Generating Locales. (See [this thread]("http://www.ubuntuforums.org/showthread.php?t=264175") for details on that one.) I really would like to install it, but since it can't get past Generating Locales for some reason...

Anyhow, how do I solve the
```
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory 
```
problem first? I think a something.d file was removed from a locales folder, which was also removed, but I can't recall where it was (this during the uninstall of the english pack in attempt to see if reinstalling it fresh would help). I think it was after this file went away, the above error came up.

I would guess the 
```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US:en_GB:en",
        LC_ALL = (unset)
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
```

Won't be fixed until I can get the english pack to install, so I'll live with that one for the moment.

---

