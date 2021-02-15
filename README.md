# Pachyderm-Image-Tracer
Deploying a Pachyderm pipeline to detect edges of photos and output the results.


## Tutorial source: https://docs.pachyderm.com/latest/getting_started/beginner_tutorial/ 
This tutorial will show users how to deploy a Pachyderm pipeline to detect edges of photos and output the results.

Users must have Pachyderm running locally or sign up on the Pachyderm website to run Pachyderm.
- To deploy locally: https://docs.pachyderm.com/latest/getting_started/local_installation/ 
- To deploy via website: https://www.pachyderm.com/ 

## Creating a Repo:
- Within the terminal / command prompt, type “pachctl create repo images” to create a pachyderm repository called images
- You can check if the repository was created by typing “pachctl list repo”.

## To add data to pachyderm:
- Use the command in the command prompt:” pachctl put file images@master: -f example.png”.
- Use “pachctl list repo” to check that the data has been added to the repo.

## To view the file in the commit:
- Use the command “pachctl list file images@master”

## To view the added file:
- macOS: “pachctl get file images@master:example.png | open -f -a //Applications/Preview.app
- Linux 64-bit: “pachctl get file images@master:example.png | display”

## Creating a pipeline:
- Access github for pipeline source: https://github.com/pachyderm/pachyderm/blob/master/examples/opencv 
- Use the command: pachctl create pipeline -f https://raw.githubusercontent.com/pachyderm/master/examples/opencv/edges.json
- Users can view the pipeline job by typing “pachctl list job”
- Type “pachctl list repo” to make sure that the edges repo was created and stores the edges pipeline.

## Reading the Output:
- macOS: pachctl get file edges@master:example.png | open -f -a /System/Applications/Preview.app
- Linux 64-bit: pachctl get file edges@master:example.png | display

## Pachyderm Tracing
- The team made the approach of using Pachyderm to trace images in order to use these images as adversarial ones. The team had recognized that some of the successful adversarial images that were found online looked very similar to faces. By creating traced images of faces, the team can mimic a similar pattern that may disrupt recognition.
