# my_project
- 컨테이너 기반 구조 조정
- Docker Compose로 프로젝트 세팅
- web <-> was <-> db
- db는 현재 포지션만 차지하고 있음. 실제 사용 x
- 전제 조건
    - 컨테이너 기반 이미지를 저장할 저장소 및 공유 플랫폼 필요
        - 현재 hub.docker.com 활용
        - 차후 AWS ECR 활용
    - EC2 서버에 Docker 설치 필요
        - Docker 설치
        - 스펙 상향
            - t3.micro 인스턴스 유형, 2 Cpu 1 Rem, 30 Gib
            - 메모리 증설 -> 스왑 메모리 4G 증가 처리
    - deploy.yml 
        - CI/CD 설정 파일 업그레이드

# 구조
my_project/

# docker 기반 CI/CD 조정
- docker compose.yml 조정
    - app, proxy 파트 이미지를 hub 쪽으로 조정, volume 제거
- 명령어
    - docker-compose down
    - docker-compose up -d
        - --build는 제거