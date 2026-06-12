---
title: "ftp indexing"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by kane77 on 2007-02-08
anybody knows of a program (script) that would scan the ftp for files (changes) and then export it into file??

(which would then be parsed into mysql database.. but I can parse that in php...)??

---

### Post by hmLyons on 2007-02-11
I have written something similar to what you are describing in PHP. In case this would be of any use to you I'll post it here. It doesn't go as far as the solution that you are talking about but it will print out every file and modification date on the ftp server.

[PHP]
<?php

$ftp = ftp_connect("127.0.0.1");
if ( ftp_login($ftp, "username", "password") ) {
	recurse_folder($ftp, null);	
}

ftp_close($ftp);

# Print list of files in $dir, recurse into subfolders
function recurse_folder($ftp, $dir) {
	foreach ( ftp_nlist($ftp, $dir) as $f ) {
		$mod_time = ftp_mdtm($ftp, $dir);
		if ( $mod_time == -1 ) {
			# no modification date, it's a directory
			recurse_folder($ftp, $f);
		} else {
			# it's a file
			print $f . ", modtime: " . $mod_time . "\n";
		}

	}
}

?>
[/PHP]

---

### Post by kane77 on 2007-02-13
> **hmLyons said:**
> I have written something similar to what you are describing in PHP. In case this would be of any use to you I'll post it here. It doesn't go as far as the solution that you are talking about but it will print out every file and modification date on the ftp server.

[PHP]
<?php

$ftp = ftp_connect("127.0.0.1");
if ( ftp_login($ftp, "username", "password") ) {
	recurse_folder($ftp, null);	
}

ftp_close($ftp);

# Print list of files in $dir, recurse into subfolders
function recurse_folder($ftp, $dir) {
	foreach ( ftp_nlist($ftp, $dir) as $f ) {
		$mod_time = ftp_mdtm($ftp, $dir);
		if ( $mod_time == -1 ) {
			# no modification date, it's a directory
			recurse_folder($ftp, $f);
		} else {
			# it's a file
			print $f . ", modtime: " . $mod_time . "\n";
		}

	}
}

?>
[/PHP]

Thanx a lot.. I might use some of it, although I found a package ftpcopy that contains a program ftpls that would ls the structure of ftp (even recursively)

I'm not sure however how do I work with php scripts in command line...?

---

### Post by hmLyons on 2007-02-17
Thanks for the mention of the [ftpcopy]("http://www.ohse.de/uwe/ftpcopy/ftpcopy.html") program. I've been looking for a program like this but never found it before.

You can run php programs from the command line just like this,
```
php myphpfile.php
```

---

