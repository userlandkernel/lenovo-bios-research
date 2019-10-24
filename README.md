# lenovo-bios-research
Research on the Lenovo BIOS firmware.

## Introduction
As a passionate about the Darwin Kernel (XNU) and Apple's Operating System I wanted my Lenovo Ideapad 300-15isk (PARIS) to run a custom BIOS.  
The reason for this is that the BIOS that came with the device did not meet my demands of capabilities that are needed for hackingtoshing my device.  
This is why I decided to analyze the BIOS firmware to see what was hidden from me.  
I had no experience with any BIOS before, not BIOS hacking but couldn't find a decent tutorial to do it on any forum for my specific model.  
That's why decided to take the fun trip of potentially finding lenovo internal capabilities and researching the BIOS.  

## Ongoing process!
This research isn't finished, it has just started but this repository will be updated live with new findings and anyone can contribute to it but note that redistributing proprietary source code is not permitted.  
You can always reach me via twitter (@userlandkernel) if you have questions or additions as well.  

## Tools useful for this research
- Sigcheck64 (Windows Internals, for analyzing file signatures)
- Strings (For finding human-readable strings in files)
- binwalk (For finding signatures in files and extracting, analyzing firmware, entropy analysis)
- uefi-firmware-parser (For extracting and retrieving EFI firmware information from EFI files, the lenovo bios is an UEFI one)
- pestudio (For analyzing PE Executables)
- 

## Steps taken
- Downloaded the firmware (https://download.lenovo.com/consumer/mobiles/d5cn47ww.exe, backup: http://web.archive.org/web/20191023235729/https://download.lenovo.com/consumer/mobiles/d5cn47ww.exe)  
- Extraction after extraction and analysis, more and more of the firmware is retrieved from the exe file  
- UEFI extraction by uefi-firmware-parser of recovered efi files from binwalk  


## Outcomes
- Lenovo uses Insyde BIOS
- This firmware version comes with Insyde Flash Utility (iscflash) version 5.2.1.1
- bios.fd contains the actual firmware images
- Some mcrypt encrypted (blowfish algorithm) data was found
- Found a potential backdoor in the Lenovo BIOS (Pretty much in plain UEFI sight)
- Seems like the Intel Firmware Update Utility version 8.0.10.1464 is also present in this BIOS firmware image.
- The firmware update seems to go through without any physical steps needed such as copying to a USB, perhaps malware can abuse this feature?
- Possibly the Intel Management Engine is also present in the image.
