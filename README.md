split_boot_img
==============

*Python script to split Android boot.img files.*


http://linuxclues.blogspot.com/2012/11/split-bootimg-python-android.html


In Android systems kernel and initial ramdisk filesystem are usually joined 
into an only file, named boot.img, and flashed into the device.

**mkbootimg** is the tool which builds a boot.img file from its kernel and ramdisk parts.


EXECUTE SPLIT_BOOT_IMG.PY SCRIPT

This splits boot.img, create parts directory and stores there zImage (kernel) and ramdisk.gz.
    $ python split_boot_img.py -i boot.img -o parts

E.g: Splitting a boot.img file from my Samsung S5570 tass device shows this result:
    $ python split_boot_img.py -i boot.img -o foo -v

<pre>
input file: boot.img
output directory: foo

Creating directory: foo
boot_magic correct:  ANDROID!
kernel size: 3627948
kernel address: 325091328
Base: 325058560  (hex): 0x13600000
ramdisk size: 3155625
ramdisk address: 341835776
second size: 0
second address: 340787200
tags address: 325058816
page size: 4096
product name:  
cmdline:  
File foo/zImage written (length=3627948).
File foo/ramdisk.gz written (length=3155625).
</pre>

To rebuild boot.img file (in my tass device):
    $ mkbootimg --kernel zImage --ramdisk ramdisk.gz --base 13600000 --pagesize 4096 -o boot.img.new




