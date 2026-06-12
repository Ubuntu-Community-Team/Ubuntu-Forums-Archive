---
title: "Printing output of script to file?"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by meniscus on 2007-01-16
Im running this script from crontab every half hour. How do you modify this code to print to a text file on the desktop instead of the terminal? (without overwriting the temperature values)



```
#!/usr/bin/perl

{

	
	my $output = `sensors`;
	my $temp;
	if ( $output =~ /CPU Temp:\s*\+(\d+)/ ) {
    	$temp = $1; }
	
	print "$temp\n"; 
	
}

```

---

### Post by earobinson on 2007-01-16
```
(command to run script of file) > (file name you want to send the output to) 
```

---

### Post by ComplexNumber on 2007-01-16
if you use ">", this will overwrite the last output each time the script is started. to append to the same  file each time the script is run, use ">>".

---

### Post by meniscus on 2007-01-16
thanks

---

