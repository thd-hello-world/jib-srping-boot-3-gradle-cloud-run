Jib has been pretty helpful for me as a Fullstack Engineer so thought I'd contribute a little - I was having trouble getting Spring Boot 3.0.2 + Gradle + Java 17 working on GCP Cloud Run, but finally got something working, here it is...

1. If you have questions, I try to keep up on stackoverflow, ratttazelee@gmail.com/tazelee
2. I'm not a Jib or Spring expert, but I did stay at a Holiday Inn Express one time while attending a conference that Rod Johnson presented at
3. this will get you an image deployed to your GCP GCR or Artifact Registry docker repo, from which you can deploy to Cloud Run - not full CI/CD to Cloud Run because that's a whole lotta extra effort (checkout the cloudbuild.yaml file, very simple/basic
4. this is half-baked proof of concept, but it works
5. Spring Boot 3.+ moved to new jakarta package (vs older javax) for servet api references (Spring Boot defaults to Tomcat, sweeet), so you'll need to update the .java files accordingly to replace javax.xyz with jakarta.xyz (I'm gonna try to do that so by the time you clone this you may not have to)
6. Notice that in the build.gradle file, in the Jib extension/task, that only the "to" image is specified, and not the "from" image.  Jib has defaults it'll try to use to pick an appropriate base image (which is usually pretty small and ver low in vulnereabilities).  This is important for you to understand, what base image Jib is using (please see point # 4)
