# SFML_Collision
Простой движок столкновения обьектов на SFML C++

https://github.com/sxfour/SFML_Collision/assets/112577182/2aff762f-9fa5-40e6-bfef-5742241cf665


# Функция столкновения обьектов
int checkCollision(sf::RectangleShape& R1, sf::CircleShape& C1) {
    float closestX = clamp(C1.getPosition().x, R1.getPosition().x, R1.getPosition().x + R1.getSize().x);
    float closestY = clamp(C1.getPosition().y, R1.getPosition().y, R1.getPosition().y + R1.getSize().y);

    float distanceX = C1.getPosition().x - closestX;
    float distanceY = C1.getPosition().y - closestY;

    float distanceSquared = (distanceX * distanceX) + (distanceY * distanceY);
    if (distanceSquared < C1.getRadius() * C1.getRadius() && closestX != C1.getPosition().x && closestY != C1.getPosition().y) {
        return 3;
    }
    else if (distanceSquared < C1.getRadius() * C1.getRadius() && closestX == C1.getPosition().x) {
        return 2;
    }
    else if (distanceSquared < C1.getRadius() * C1.getRadius() && closestY == C1.getPosition().y) {
        return 1;
    }
    else {
        return 0;
    }
}
