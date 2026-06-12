---
title: "Can't install Karmic on late 09 iMac"
date: 2009-11-06
forum: Apple Hardware Users
---

### Post by janjokela on 2009-11-06
Hi, I'm sorry case there is a thread that already covers this issue. I did search the forums :)

I am having trouble installing Karmic on a late 2009 iMac. I get the ubuntu logo when booting but it doesn't enter the installer nor a live-cd session. It falls back to cli and the screen starts flickering. The last messages I get are about disabling app-armor profiles, but no errors so I guess that's not related. Trying to start gdm fails to start an X session. So I guess this is some kind of Xorg issue.

I have tried both 32bit and 64bit and both with acpi off.

Thanks in advance,
Jan.

---

### Post by janjokela on 2009-11-06
Problem solved :)

For those looking for a workaround, start the live session or installation with the option 'xforcevesa', which will force the use of vesa driver as opposed to the radeon one.

After installation, enable the proprietary 'fglrx' driver. It will enable you to use the screen native resolution and offer 3D support. 

As a side note, things that don't work out of the box are sound, screen brightness adjustment and the multi touch part of the magic mouse (only pointing and clicking works).

Cheers.

---

### Post by Exirion on 2009-11-10
I patched some existing code for display brightness control. The original code worked for the previous generation and with the minor (port number) adjustments I made it works for the late 2009 models :)

```

/*
 * Apple Macbook Pro LCD backlight control
 *
 * Copyright (C) 2006 Nicolas Boichat <nicolas @boichat.ch>
 * Copyright (C) 2006 Felipe Alfaro Solana <felipe_alfaro @linuxmail.org>
 *
 * This program is free software; you can redistribute it and/or modify
 * it under the terms of the GNU General Public License as published by
 * the Free Software Foundation; either version 2 of the License, or
 * (at your option) any later version.
 *
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU General Public License for more details.
 *
 * You should have received a copy of the GNU General Public License
 * along with this program; if not, write to the Free Software
 * Foundation, Inc., 675 Mass Ave, Cambridge, MA 02139, USA.
 *
 */

#include <stdio.h>
#include <sys/io.h>
#include <stdlib.h>

void init()
{
    if (ioperm(0x52e, 0x52f, 1) < 0)
    {
        perror("ioperm failed (you should be root).");
        exit(2);
    }
}

int get_current_value()
{
    outb(0x03, 0x52f);
    outb(0xBF, 0x52e);
    char t = inb(0x52f) >> 4;
    return t;
}

int calculate_new_value(const char *arg)
{
    int val, new = atoi(arg);

    if (arg[0] == '+' || arg[0] == '-')
        val = new + get_current_value();
    else
        val = new;

    if (val > 15)
        val = 15;
    else if (val < 1)
        val = 1;

    return val;
}

int main(int argc, char** argv)
{
    if (argc > 2)
    {
        printf("Usage:\n");
        printf("%s : read current value\n", argv[0]);
        printf("%s value : write value [0-15]\n", argv[0]);
        exit(1);
    }

    init();

    if (argc < 2)
    {
        printf("Current value : %d\n", get_current_value());
        exit(0);
    }

    if (argc == 2)
    {
        int value = calculate_new_value(argv[1]);
        outb(0x04 | (value << 4), 0x52f);
        outb(0xBF, 0x52e);
        printf("new value: %d\n", value);
    }

    return 0;
}

```

---

