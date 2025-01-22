# This fork is for those people who have a respeaker lite with soldered xiao esp32-s3 and wish to use the Koala case with the led light ring.
## To accomplish this:
   1. Print the newfaceplate.step file. As the esp32 does not support the use of the volume control, this removes that control and adds a home assistant logo.
   2. Solder the led strip to pin 1 of the esp32 and the 5V and ground pads on the side of the respeaker lite
   3. Use the included newyaml.yaml file in home assistant. Add your encryption key to the file and change the name to anything you desire.
   4. That's it, enjoy the improved sound and HA lighting control of koala!
 <img src="/casing/images/koala1.jpg" width="400">
Watch the video of respeaker in action with music assistant: Don't be too concerned about response time, my internet is slow.... (https://www.youtube.com/shorts/Wk3J1GyNItQ)

# UPDATE: I have managed to include the Koala KY040 encoder to allow the use of the original casing and have full volume control. The KY040 pushbutton also allows for creating another event based home assistant automation. in combination with the existing respeaker lite pushbutton automation, this allows for up to 7 events from the pushbuttons on the media player for home assistant to respond to! (1 single press, 2 double presses, 2 triple presses and 2 long presses)

# To accomplish all this I have added a d1 mini to control the koala KY040 encoder.
The D1 mini is inside the koala case, and communicates with the koala media controller via home assistant.  
This allows the respeaker lite with embedded esp s3 to use the koala encoder for volume control!  
An additional benefit is the encoder pushbutton actions have been added to home assistant as events that can be included in automations.  
The button appears very stable and the D1 mini does not appear to have the  debouncing issues that formatbce reported with using the external ESP s3.  
An example automation to illustrate the use of the encoder pushbutton is included, see: "example ha automation.yaml"  The events are 'single_press', 'double_press' 'triple_press' and 'long_press'

the esphome config for the d1 mini is provided as: 'encoder.yaml'   
change the wifi ssid and media player name. 
The wiring is straightforward:  

Vbus - 5V  
GND - GND  
gpio0 - SW  
gpio4 - CLK  
gpio5 - DT  


 <img src="/casing/images/encoder1.jpg" width="400">
  <img src="/casing/images/encoder2.jpg" width="400">
   <img src="/casing/images/encoder3.jpg" width="400">

Simply connect the d1 mini and add it to the original case.
# important: In the esphome home assistant configuration for the d1 mini encoder, click on configure and select "Allow the device to perform Home Assistant actions" or it will not work!


[formatbce's original documentation follows:]

[!["Buy Me A Coffee"](https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png)](https://www.buymeacoffee.com/formatbce)

# Koala Satellite
<div style="display: flex; justify-content: space-between;">
  <img src="/casing/images/assembled.png" width="400">
  <img src="/instructions/images/live_view_old.jpg" width="400">
</div>

### Koala Satellite is a DIY device that works as a satellite for Home Assistant Assist.

#### Main characteristics:
- two far-field microphones, coupled with XMOS chip XU-316 for noise cancelation and voice recognition;
- 16bit 48kHz audio output;
- 5W speaker to use for speech responses, announcements, chimes or music;
- hardware mute button;
- rotary encoder for volume change and other adjustments;
- LED strip for status displaying or mood lighting;
- 3.5mm line-out jack to connect external speaker.

#### Appreciation
I'd like to thank to NabuCasa team and Home Assistant project - this project firmware is almost completely based on their work, and created for Home Assistant exclusively.
My dedicated appreciation goes to the  [Voice PE](https://github.com/esphome/home-assistant-voice-pe) team, that made all of this possible.
Also, i'm thankful for continuous support from Seeed developers. We spent days debugging Respeaker Lite software. Now it works great!

#### How is it different from Home Assistant [Voice PE](https://www.home-assistant.io/voice-pe)?
They're actually pretty similar. I used PE ESPHome software as the base for Koala software, and many parts are working identically.
They connect to Home Assistant in the same way and have identical possibilities.
Koala is just something you can assemble yourself from widely accessible parts.
Also it has pretty decent for size audio speaker and doesn't have external sensors connectors.

#### How is it different from [this repository](https://github.com/formatBCE/Respeaker-Lite-ESPHome-integration)?
I started to work with [Respeaker Lite](https://www.seeedstudio.com/ReSpeaker-Lite-p-5928.html) several months ago. 
That repository was my attempt to put everything i know together.
All the process is pretty much documented in [this Home Assistant Community thread](https://community.home-assistant.io/t/respeaker-lite-new-seeed-studio-voice-assistant-development-kit-hardware-combine-esp32-with-xmos-xu316-dsp-chip-for-advanced-audio-processing-as-a-esphome-based-home-assistant-assist-satellite-voice-devkit).
At some point i made Echo-Pop-like enclosure to the Respeaker Lite Kit. But it had disadvantages, like gluing face plate (or fabric), no access to ESP and Respeaker USB ports, lack of volume controls and rudimentary LED.
So i started thinking on real device. Here it is.

#### Why not use [Respeaker Lite with pre-soldered XIAO ESP32-S3 board](https://www.seeedstudio.com/ReSpeaker-Lite-Voice-Assistant-Kit-p-5929.html)? Isn't that easier and cheaper?
Yes, it is. But pretty much all exposed ESP GPIO pins are used by Respeaker in that configuration. So there's no way to use more elements like rotary or LED strip.
Also, current configuration hides nicely USB power cable (which is also ESP32 data cable), and allows exposing RESET/BOOT buttons for flashing.

### [Here's how you make one for yourself.](/instructions/assembly.md)

### What if i don't want or cannot build it myself?
Create issue in this repository to let me know, that you need fully assembled device (or just printed enclosure for it). I will consider selling if demand is there. :)
